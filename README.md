# smtp_email_spoofer
Python 3.x based email spoofer 

> *For educational purposes only. Do not send to or from addresses that you do not own.* 

> Email spoofing is often used for spam campaigns and phishing attacks. If you use this tool inappropriately, you could violate of the [CAN-SPAM Act of 2003](https://en.wikipedia.org/wiki/CAN-SPAM_Act_of_2003) and/or the [Computer Fraud and Abuse Act](https://en.wikipedia.org/wiki/Computer_Fraud_and_Abuse_Act). You'd also be committing [wire fraud](https://en.wikipedia.org/wiki/Mail_and_wire_fraud#Wire). **Use your head**.

----

## Table of Contents

- [Getting Started](#getting-started)
- [Commands](#commands)
  - [Wizard](#wizard)
  - [CLI](#cli)

## <a id="getting-started">Getting Started</a>

1. `$ git clone https://github.com/yahav-h/smtp_email_spoofer.git`
3. Activate `virtualenv`
2. `$ pip install -r requirements.txt`
3. `$ python spoof.py`

## <a id="commands">Commands</a>

`smtp-email-spoofer-py` offers two global commands: [`wizard`](#wizard) and [`cli`](#cli):

```bash
$ py spoof.py -h
usage: spoof.py [-h] {wizard,cli} ...

Python 3.x based email spoofer

optional arguments:
  -h, --help    show this help message and exit

commands:
  {wizard,cli}  Allowed commands
    wizard      Use the step-by-step wizard
    cli         Pass arguments directly
```    

----

### <a id="wizard">Wizard</a>

Issue the `wizard` command to use the step-by-step wizard:

```
$ py spoof.py wizard
```

1. Enter the SMTP server information to establish a connection over TLS - you'll need to enter the HOST and PORT

2. Optionally provide credentials to login to the SMTP server - use email credentials

3. Compose the forged message - either select a template like `exmaple.html` / `phishing_ex.html` or create your own from the shell.

> Load the HTML message body from a file, or compose it within the shell

4. Send the message

----

### <a id="cli">CLI</a>

Issue the `cli -h` command to view the help:

```bash
$ py spoof.py cli -h
usage: spoof.py cli [-h] (--noauth | --username USERNAME)
                    [--password PASSWORD] --host HOST --port PORT --sender
                    SENDER --name NAME --recipients RECIPIENTS
                    [RECIPIENTS ...] --subject SUBJECT --filename FILENAME

optional arguments:
  -h, --help            show this help message and exit
  --noauth              Disable authentication check
  --username USERNAME   SMTP username
  --password PASSWORD   SMTP password (required with --username)

required arguments:
  --host HOST           SMTP hostname
  --port PORT           SMTP port number
  --sender SENDER       Sender address (e.g. spoofed@domain.com)
  --name NAME           Sender name (e.g. John Smith)
  --recipients RECIPIENTS [RECIPIENTS ...]
                        Recipient addresses (e.g. victim@domain.com ...)
  --subject SUBJECT     Subject line
  --filename FILENAME   Message body filename (e.g. example.html)
  --headers HEADERS     Message headers (e.g. '{"MY-HEADER : MY-VALUE"}')
```

1. Issue the `cli` command along with the appropriate arguments:

> If `--noauth` is not specified, `--username` and `--password` are required.
