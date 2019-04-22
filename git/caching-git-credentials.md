# Caching your Git Credentials

I grew tired of having to enter again and again my extremely long password.
If only I had dared to Google this issue sooner, it would have saved me a lot of hassle.

Simply run this command to cache your credentials:

```bash
$ git config --global credential.helper cache
# Set git to use the credential memory cache (15 min)

$ git config --global credential.helper 'cache --timeout=3600'
# Set the cache to timeout after 1 hour (setting is in seconds)
```

And you're set for an hour! (or more)

---
TIL #3 - 22/04/2019
