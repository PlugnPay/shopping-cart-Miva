04/15/2002
		Miva NT Installation

1.  Installing payment method.


Using Miva Mia:
  a.  Copy the pnpmiva.dll onto your server.

  b.  Right click the miva mia icon in your system tray and select properties.

  c.  A window will open.  Click the tab labeled commerce.

  d.  Click the add button and a new window will open.

  e.  Click the browse button and locate the pnpmiva.dll file on your system.

  f.  Enter "PlugNPay" as the name for the Method. 

Using Miva Empressa:

  a. Windows NT 4.0 installation
     
     1.  click on start
         click on programs
         click on "Windows NT 4.0 Option Pack"
         click on "Microsoft Internet Information Services"
         click on "Internet Service Manager"

  b. Windows 2000 installation

     1.  click on start
         click on settings
         click on control Panel
         click on "Administration Tools"
         click on "Internet Information Services"

     2.  Select your webserver from the list. Right click on it
         and select properties.

     3.  Select the Miva Engine tab.

     4.  Click on the Commerce Libraries button.

     5.  Click add.  A window will pop up.  The Method is
         "PlugNPay".  Click the browse button and locate the
         dll included in the miva module zip file.

     6.  Click ok now go on to the next step.

2.  Go to your miva admin screen.

    Click the arrow on modules.

    Click on add module.

    Click on the upload file button and a new window should pop up
    with a dialog to locate the plugnpay.mvc on your local machine.

    Locate the file and click the upload button.

3.  Go to your miva admin screen.

   a.  Click the Stores arrow and a list of your Stores you have setup should
    appear.

   b.  Click the arrow next to the store you want to use the plugnpay payment
       module with.  A list should appear one of the options is Payment
       Configuration.  Click on Payment Configuration.

   c.  A list of payment options will appear with check boxes next to them.
       Select the payment option for Plug n Pay and click the update button.

4.  You are now ready to use your miva shopping cart to run transactions through
    Plug n Pay.


Common Problems:

- If you have trouble running transactions you should upgrade the 
version of wininet on the server.  This can be done by upgrading
the version of IE to the latest version of IE 5.5.

- If you receive an error message saying "method PlugNPay does not
exist" check that you typed the method in correctly it is case
sensitive.


