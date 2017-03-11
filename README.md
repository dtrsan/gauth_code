# About
**gauth_code** is a simple script that generates verification codes for Google
2-Step verification. **gauth_code** has support for storing configuration for
multiple accounts. Configuration saves at ~/.gauthrc.

# Installation
Just copy **gauth_code** somewhere on your path.

# Usage
## Generate verification code
To generate a verification code account run **gauth_code** without parameters.
Before that the account must be configured. See "*Add / update an account*" how
to configure the account.

**Example:**
```
$ gauth_code account@example.com

Account: account@example.com
-----------------------------
***....... 291337
.......... 133775
-----------------------------
```

## Add / update an account
To add an account run **gauth_code** with -s parameter.

**Example:**
```
$ gauth_code -s 3a2xv44tgvxqajn4rvw7hceuwi6rl337 account@example.com

Adding account 'account@example.com' with the new secret.

Account: account@example.com
-----------------------------
***....... 291337
.......... 133775
-----------------------------
```

## Remove an account
To remove an account run **gauth_code** with -r parameter.

**Example:**
```
$ gauth_code -r account@example.com

Trying to remove account 'account1@example.com'.
Account 'account1@example.com' is removed.

```

## List all configured accounts
To list all configured accounts run **gauth_code** with -l parameter.

**Example:**
```
$ gauth_code -l

Available accounts:
  account1@example.com
  account2@example.com

```

## Show tokens for all accounts
To show tokens for all configured accounts run **gauth_code** with -a parameter.

**Example:**
```
$ gauth_code -a

***....... 291337  account1@example.com
***....... 133775  account2@example.com
```

# Help
To see help run **gauth_code** with -h parameter.

**Example:**
```
$ gauth_code -h

Usage: gauth_code [-h] [-l] [-r | -s <secret>] <account>

Description:
  -a    Show tokens for all accounts.
  -l    List the accounts.
  -r    Remove an account.
  -s <secret>
        Add a new account or update secret for an existing account.
        Secret is a base32 encoded string.
  -h    Help.

```

# Requirement
**gauth_code** requires Python 3. It uses only Python Standard Library. No
additional installation of third party modules is required.

# FAQ
1. Is it possible to use **gauth_code** to generate a code for Dropbox two-step
   verification? **gauth_code** always throws "Invalid secret." message during
   account configuration.

**Answer:** Yes, it is but you need to pad the secret key properly. Just add
six '=' characters ("======") at the end of the secret key and everything will
work fine.

