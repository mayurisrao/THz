# wget for Windows

<p>
Make sure you have set up your Earthdata account.

* Install wget if necessary. A version of wget 1.18 compiled with gnuTLS 3.3.3 or OpenSSL 1.0.2 or LibreSSL 2.0.2 or later is recommended.
* Create a cookie file. This file will let you download GES DISC resources without having to re-login.
* Open a run-command window by pressing WinKey + R
* Next, enter "cmd" in the text field and click "OK"
* Navigate to the directory you wish to create the cookies file in. In this guide, we place it under the C drive, but any directory will do. You can navigate to the C drive by entering C:
* Finally, enter NUL > .urs_cookies.
  <br><em>Note</em>: you may need to re-create .urs_cookies in case you have already executed wget without valid authentication.
  <br><em>Note</em>: you can get 'Access denied' error. Enter 'dir' to verify that '.urs_cookies' file is listed in your directory.
  
## Download your data using wget:
### To download one file:

  >wget --load-cookies C:\\\.urs_cookies --save-cookies C:\\\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user=<your username> --ask-password <url>

  * If you are using subsetting services through the GES DISC website:

  >wget --load-cookies C:\\\.urs_cookies --save-cookies C:\\\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user= --ask-password --content-disposition <url>

* --auth-no-challenge may not be needed depending on your version of wget
* 'username' is the username belonging to your Earthdata account
* 'url' is the link that points to a file you wish to download or to an OPeNDAP resource.
* Only use --content-disposition for downloading subsetted files through the GES DISC website
* Your Earthdata password might be requested on the first download
### To download multiple data files at once 
  create a plain-text <url.txt> file with each line containing a GES DISC data file URL. Then, enter the following command:

  > wget --load-cookies C:\.urs_cookies --save-cookies C:\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user=<your username> --ask-password -i <url.txt>

  * Add the --content-disposition to your command when using subsetting services:
  
  > wget --load-cookies C:\.urs_cookies --save-cookies C:\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user= --ask-password --content-disposition -i <url.txt>

</p>

# wget for Mac/Linux
  
* Make sure you have set up your Earthdata account.
* Install wget if necessary. A version of wget 1.18 compiled with gnuTLS 3.3.3 or OpenSSL 1.0.2 or LibreSSL 2.0.2 or later is recommended.
* Create a .netrc file in your home directory.
* cd ~ or cd $HOME
* touch .netrc
* echo "machine urs.earthdata.nasa.gov login <uid> password <password>" >> .netrc (where <uid> is your user name and <password> is your Earthdata Login password without the brackets)
* chmod 0600 .netrc (so only you can access it)
* Create a cookie file. This file will be used to persist sessions across calls to wget or curl.
* cd ~ or cd $HOME
* touch .urs_cookies.
  <em>Note:</em> you may need to re-create .urs_cookies in case you have already executed wget without valid authentication.

## Download your data using wget:
  
### To download one file:
  
  > wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies <url>

* If you are using subsetting services through the GES DISC website:

  > wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies --content-disposition <url>

* --auth-no-challenge may not be needed depending on your version of wget
* 'url' is the link that points to a file you wish to download or to an OPeNDAP resource.
* Only use --content-disposition for downloading subsetted files through the GES DISC website.
* Your Earthdata password might be requested on the first download

### To download multiple data files at once

* create a plain-text <url.txt> file with each line containing a GES DISC data file URL. Then, enter the following command:
  
 > wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies -i <url.txt>

* Add the --content-disposition to your command when using subsetting services:

 > wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies --content-disposition -i <url.txt>

