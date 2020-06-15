
      ---
      title: CAPTCHA Security
      ---

      CAPTCHA stands for "**C**ompletely **A**utomated **P**ublic **T**uring test to tell **C**omputers and **H**umans **A**part". These tests are used to ensure that your site is not subjected to automated attacks/spam from bots attempting to register or log in to your site. Customers must enter the text seen in the CAPTCHA image (which computers cannot read) before they can log in:  
  
![](images/1415380373574.png)

The CAPTCHA image can be enabled on 3 pages, using the following [Settings](default.aspx?pageid=settings):

**Setting Name**

**Page**

SecurityCodeRequiredOnAdminLogin

admin/signin.aspx

SecurityCodeRequiredOnCreateAccount

createaccount.aspx (?checkout=false)

SecurityCodeRequiredOnCreateAccountDuringCheckout

createaccount.aspx (?checkout=true)

SecurityCodeRequiredOnStoreLogin

signin.aspx

The CAPTCHA image can be customized according to the requirements/desires of your site, using the following Settings:

**Setting Name**

**Description**

Captcha.AllowedCharactersRegex

This is a regular expression which determines which characters the CAPTCHA image will contain. Do not change this if you are not familiar with regular expressions!

Captcha.CaseSensitive

Setting this to true will require customers to properly match the case shown in the CAPTCHA image. Setting this to false does NOT make the CAPTCHA image not use caps in the image, it simply ignores the case for the customer entry. Disabling caps entirely would require editing the Captcha.AllowedCharactersRegex AppConfig.

Captcha.HorizontalColor

This changes the color of the horizontal 'brushstrokes' of color that are randomly generated on the CAPTCHA image.

Captcha.ImageBackColor

This is the color used for the 'block' portion of the grid background of the CAPTCHA image.

Captcha.ImageForeColor

This is the color used for the 'line' portion of the grid background of the CAPTCHA image.

Captcha.MaxAsciiValue

Do not change this unless you know what you are doing!

Captcha.NumberOfCharacters

Specifies the number of characters the CAPTCHA image will contain.

Captcha.TextBackColor

Controls the background color of the text in the CAPTCHA image.

Captcha.TextForeColor

Controls the foreground color of the text in the CAPTCHA image.

Captcha.VerticalColor

This changes the color of the vertical 'brushstrokes' of color that are randomly generated on the CAPTCHA image.
      