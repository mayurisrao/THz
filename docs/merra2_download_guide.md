# MERRA-2 Data Download Guide (`wget` + NASA Earthdata)

Instructions for downloading NASA GES DISC / MERRA-2 atmospheric datasets via `wget` on Windows and macOS/Linux.

> **Prerequisite:** Create and activate a [NASA Earthdata](https://urs.earthdata.nasa.gov/) account before downloading.

---

## Windows

1. Install `wget` if necessary (`wget >= 1.18` compiled with GnuTLS 3.3.3, OpenSSL 1.0.2, or LibreSSL 2.0.2 or later is recommended).
2. Create a cookie file so `wget` can access GES DISC resources without re-authenticating on every request:
   - Press `Win + R`, type `cmd`, and click **OK**.
   - Navigate to the directory where you want to store the cookie file (e.g., `C:`):
     ```bat
     C:
     NUL > .urs_cookies
     ```
   - *Note:* You may need to recreate `.urs_cookies` if you previously ran `wget` without valid authentication.
   - *Note:* If you get an `Access denied` error, run `dir` to verify whether `.urs_cookies` already exists in that directory.

### Download a single file (Windows)

```bat
wget --load-cookies C:\.urs_cookies --save-cookies C:\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user=<your_username> --ask-password <url>
```

If using subsetting services through the GES DISC website, add `--content-disposition`:

```bat
wget --load-cookies C:\.urs_cookies --save-cookies C:\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user=<your_username> --ask-password --content-disposition <url>
```

### Download multiple files (Windows)

Create a plain-text `<url.txt>` file containing one GES DISC URL per line, then run:

```bat
wget --load-cookies C:\.urs_cookies --save-cookies C:\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user=<your_username> --ask-password -i <url.txt>
```

With GES DISC subsetting services:

```bat
wget --load-cookies C:\.urs_cookies --save-cookies C:\.urs_cookies --auth-no-challenge=on --keep-session-cookies --user=<your_username> --ask-password --content-disposition -i <url.txt>
```

---

## macOS / Linux

1. Install `wget` if necessary (`wget >= 1.18` compiled with GnuTLS 3.3.3, OpenSSL 1.0.2, or LibreSSL 2.0.2 or later is recommended).
2. Create a `.netrc` file in your home directory with your Earthdata credentials:
   ```bash
   cd ~
   touch .netrc
   echo "machine urs.earthdata.nasa.gov login <uid> password <password>" >> .netrc
   chmod 0600 .netrc
   ```
   *(Replace `<uid>` and `<password>` with your Earthdata Login username and password without angle brackets.)*
3. Create the cookie file to persist sessions across `wget` or `curl` calls:
   ```bash
   cd ~
   touch .urs_cookies
   ```
   *(Note: You may need to recreate `.urs_cookies` if you previously ran `wget` without valid authentication.)*

### Download a single file (macOS / Linux)

```bash
wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies <url>
```

If using GES DISC subsetting services:

```bash
wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies --content-disposition <url>
```

### Download multiple files (macOS / Linux)

Create a plain-text `<url.txt>` file with one GES DISC URL per line, then run:

```bash
wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies -i <url.txt>
```

With GES DISC subsetting services:

```bash
wget --load-cookies ~/.urs_cookies --save-cookies ~/.urs_cookies --auth-no-challenge=on --keep-session-cookies --content-disposition -i <url.txt>
```

---

### Flag Notes

- `--auth-no-challenge=on` may not be needed depending on your `wget` version.
- Only use `--content-disposition` when downloading subsetted files through the GES DISC website.
- Your Earthdata password may be requested on the first download.
