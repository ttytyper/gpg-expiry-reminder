# gpg-expiry-reminder

Lists keys that have expired or are going to expire soon. This is intended to
be called as a cronjob to remind you when it's time to extend your key
validity.

## Usage:

`gpg-expiry-reminder [keyid] [keyid] [...]`

With no listed keys, gpg defaults to list all keys in your keyring. This may
or may not be what you intend. You probably want to list your own keys.

`keyid` can be anything gpg accepts for `--list-keys`, including 0xdeadbeef
notation, names, email addresses, etc.

This script only needs access to your public key. No need for your private
key. The script ignores invalid, disabled and revoked keys, as well as keys
with unknown/unset validity.

Optionally use env variable acceptableexpirydays to the number of days of
notice you want. Make sure this gives you enough time to edit and publish
your key, as well as for your contacts to refresh their copies. Default: 30

## Exit values

* 0 when all listed keys are good for at least $acceptableexpirydays days
* 1 when any listed key needs its expiry extended soon

