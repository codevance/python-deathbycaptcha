# Python Death By Captcha

Python wrapper for Death By Captcha API http://www.deathbycaptcha.com/

## How to install

```
pip install git+https://github.com/codevance/python-deathbycaptcha.git
```

## Example
```python
import deathbycaptcha

    # Put your DBC account username and password here.
    # Use deathbycaptcha.HttpClient for HTTP API.
    client = deathbycaptcha.SocketClient(username, password)
    try:
        balance = client.get_balance()

        # Put your CAPTCHA file name or file-like object, and optional
        # solving timeout (in seconds) here:
        captcha = client.decode(captcha_file_name, timeout)
        if captcha:
            # The CAPTCHA was solved; captcha["captcha"] item holds its
            # numeric ID, and captcha["text"] item its text.
            print "CAPTCHA %s solved: %s" % (captcha["captcha"], captcha["text"])

            if ...:  # check if the CAPTCHA was incorrectly solved
                client.report(captcha["captcha"])
    except deathbycaptcha.AccessDeniedException:
        # Access to DBC API denied, check your credentials and/or balance
```