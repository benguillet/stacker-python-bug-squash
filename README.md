# Python bug squash

One of our internal tools includes hooks to perform functions like building AWS lambda payloads from a configuration file and uploading them to S3.

The content hash generated by the AWS lambda hook seems to change periodically, and is different across machines even when nothing else has changed. The expected behaviour of the hook is for the generated payload to be uploaded only when it the user configuration has changed. So if the hook is run on two separate machines for the same configuration file the resulting payload should only be uploaded once.

## Running the tests

First make sure you have pip & virtualenv installed.  If not, then perform the following:

```
easy_install pip
pip install --upgrade pip
pip install virtualenv
```

Now instantiate a virtualenv and activate it:

```
virtualenv remind-bug-squash
. ./remind-bug-squash/bin/activate
```

Now install all the necessary dependencies:

```
pip install -r requirements.txt
```

You should now be able to run the test suite from the top level directory of the repo:

```
nosetests
```
