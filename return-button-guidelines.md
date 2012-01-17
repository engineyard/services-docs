# Putting return-to-Engine-Yard buttons on your page

If you are integrating your platform service with Engine Yard Cloud, you must to place return-to-Engine-Yard buttons on your application pages so that users can return to the Engine Yard UI. 

This document describes how to create these buttons. 

You can choose to code your "buttons" as href link, button, or input (type submit) elements. This [page](http://engineyard.github.com/services-docs/return_button_examples.html) shows an example of each. 

## To put a return-to-Engine-Yard button on your page  

1. Add this CSS to your page or style sheet. (This CSS adds the button class "ey-return" to a button, href link, or input element.) 

        <style type="text/css">
        button.ey-return, input.ey-return, a.ey-return {
          font: 12px/1.5 "Lucida Sans Unicode", "Lucida Grande", Verdana, Arial, Helvetica, sans-serif;
          text-shadow: 0 1px 2px white;
          text-decoration: none;
          color: #444;
          cursor: pointer;
          -webkit-box-shadow: 0px 1px 2px #999999;
             -moz-box-shadow: 0px 1px 2px #999;
                  box-shadow: 0px 1px 2px #999;
          background-color: #FFFFFF;
          background-image: -webkit-gradient(linear, left top, left bottom, from(#FFFFFF), to(#CCCCCC));
          background-image: -webkit-linear-gradient(top, #FFFFFF, #CCCCCC);
          background-image:    -moz-linear-gradient(top, #FFFFFF, #CCCCCC);
          background-image:     -ms-linear-gradient(top, #FFFFFF, #CCCCCC);
          background-image:      -o-linear-gradient(top, #FFFFFF, #CCCCCC);
          background-image:         linear-gradient(top, #FFFFFF, #CCCCCC);
          border: 1px solid #CCC;
          border-bottom-color: #BFBFBF;
          vertical-align: baseline;
          position: relative;
          display: inline-block;
          margin: 0;
          border-radius: 24px;
          font-size: 15px;
          line-height: 1.25;
          padding: 6px 24px;
        }
        button.ey-return:hover,
        a.ey-return:hover,
        input.ey-return:hover {
          background-color: #F2F2F2;
          background-image: -webkit-gradient(linear, left top, left bottom, from(#F2F2F2), to(#BDBDBD));
          background-image: -webkit-linear-gradient(top, #F2F2F2, #BDBDBD);
          background-image:    -moz-linear-gradient(top, #F2F2F2, #BDBDBD);
          background-image:     -ms-linear-gradient(top, #F2F2F2, #BDBDBD);
          background-image:      -o-linear-gradient(top, #F2F2F2, #BDBDBD);
          background-image:         linear-gradient(top, #F2F2F2, #BDBDBD);
          border: 1px solid #bdbdbd;
        }
        .ey-return img {
          margin: 0 0 -3px 1px;
          padding: 0;
        }
        </style>

2. Choose which element you want to use for your return-to-Engine-Yard button, for example:  

    * If your configuration process uses a form that ends with a submit button that returns users back to the Engine Yard UI, use the button element with the text "Save and return to" for your form's submit button.
    * If you have your own landing page at the end of the configuration process, use the href link element with the text "Return to".

3. Copy-and-paste one of the templates below into your page. Edit the text if necessary.



## Templates

Use the following HTML code as templates for the return-to-Engine-Yard buttons on your page. 

**Note:** You may modify the text if necessary. However, please do not alter the CSS style or logo. 

### **href link** elements

    <a href="returnlink" class="ey-return">Return to <img src="http://www.engineyard.com/images/engine_yard_icon.png" alt="Engine Yard" /></a>

### **button** elements

    <button class="ey-return">Save and return to <img src="http://www.engineyard.com/images/engine_yard_icon.png" alt="Engine Yard" /></button>

### **input type="submit"**

    <input type="submit" class="ey-return" value="Save and return to Engine Yard">
