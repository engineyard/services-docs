# Putting a "Return to Engine Yard" button on your page

Please put one of these buttons on your page, so that the user knows to
return to Engine Yard and complete the setup process.

Checkout some [examples](http://engineyard.github.com/services-docs/return_button_examples.html).

## Automatically redirecting?

Use "Save and return to Engine Yard" as your form's submit button.

## Have your own landing page?

Use the "Return to Engine Yard" link.

## The CSS that you'll need

Add the following block of CSS to your page.

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

# HTML

Add the button class "ey-return" to a button, href, or input element.

## Examples

### **button** elements

    <button class="ey-return">Return to <img src="https://cloud.engineyard.com/images/icons/engine_yard_icon.png" alt="Engine Yard" /></button>

    <button class="ey-return">Save and return to <img src="https://cloud.engineyard.com/images/icons/engine_yard_icon.png" alt="Engine Yard" /></button>

### **a href** elements

    <a href="returnlink" class="ey-return">Save and return to <img src="https://cloud.engineyard.com/images/icons/engine_yard_icon.png" alt="Engine Yard" /></a>

### **input type="submit"**

    <input type="submit" class="ey-return" value="Save and return to Engine Yard">
