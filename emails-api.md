#e-mails in the add-ons api.

This is a "beta" feature, I have yet to confirm a partner successfully and completely integrating with it. Please let me know if you have any problems integrating with it.

That said, it is tested and it should work.

So the problem with simply providing an e-mail to the partner is that the e-mail could change.  We solve it with notifications.  Thus, we will only send you e-mail address if you have implemented support for notifications.

To support notifications, send a "users_url" along with your response to service account creation.
Example:

    ApiHMAC -> POST (http://mock.service/api/1/service_accounts_callback)
    -> service_provider
    {"name"=>"some-account",
     "url"=>
      "http://services.engineyard.com/api/1/partners/20/services/21/service_accounts/23",
     "messages_url"=>
      "http://services.engineyard.com/api/1/partners/20/services/21/service_accounts/23/messages",
     "invoices_url"=>
      "http://services.engineyard.com/api/1/partners/20/services/21/service_accounts/23/invoices"}

    ApiHMAC <--200-- service_provider
    {"service_account"=>
      {"url"=>"http://mock.service/api/1/account/123",
       "configuration_required"=>false,
       "configuration_url"=>"http://mock.service/sso/account/123",
       "provisioned_services_url"=>
        "http://mock.service/api/1/account/123/provisioned_services_callback",
       "users_url"=>"http://mock.service/api/1/accounts/123/users"},
     "message"=>
      {"message_type"=>"status", "subject"=>"some messages", "body"=>nil}}

Notice that the returned JSON includes a "users_url" specific to the account that was created.  Now Engine Yard has a URL it can use to post updates if any information about the users on that account changes.

When the User then SSO's to the parter addon, the e-mail will be included. For example:

    ApiHMAC -> GET (http://mock.service/sso/account/123?access_level=owner&ey_return_to_url=https%3A%2F%2Fcloud.engineyard.com%2Fdashboard&ey_user_email=the-one-user%40example.com&ey_user_id=2164740220&ey_user_name=Person+Name&timestamp=2012-05-11T11%3A23%3A52-07%3A00&signature=AuthHMAC+123edf%3A8AuxfLpndgtIojrwmTBYoARXs1I%3D)
    -> service_provider
    ApiHMAC <--200-- service_provider

The partner gets the email along with id and name and can save this info.

When/If the user changes their e-mail address, we will make a GET request to the users_url we have for the addon, and determine if that update needs to be propagated to the addon.  For example:

    ApiHMAC -> GET (http://mock.service/api/1/accounts/123/users) ->
    service_provider
    ApiHMAC <--200-- service_provider
    [{"user"=>
       {"access_level"=>"owner",
        "ey_user_id"=>"2164740220",
        "ey_user_email"=>"the-one-user@example.com",
        "ey_user_name"=>"Person Name"},
      "url"=>"http://mock.service/api/1/accounts/123/users/2164740220"}]

We see all the information the partner has saved.  In this case, it included a different e-mail, so we make a PUT request to change it.

    ApiHMAC -> PUT (http://mock.service/api/1/accounts/123/users/2164740220)
    -> service_provider
    {"user"=>{"ey_user_email"=>"new_email@example.com"}}

    ApiHMAC <--200-- service_provider
    {}

Thus, to summarize. You will need to: 

* Provide a "users_url" on account setup and respond to authenticated GETs to that URL with the format EY expects.
* Include in the users_url response the current e-mail and a "url" to which we can PUT updated for EACH user.
* Support PUT requests to the url returned in #2 and properly update your records.

For further example of how the e-mails API works, see [this test in `ey_services_api`](https://github.com/engineyard/ey_services_api/blob/master/spec/users_spec.rb#L10).
