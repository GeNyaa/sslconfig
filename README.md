sslconfig
=========

CloudFlare's Internet facing SSL cipher configuration

This repository tracks the history of the SSL cipher configuration used for
CloudFlare's public-facing SSL web servers. The repository tracks an internal
CloudFlare repository, but dates may not exactly match when changes are made.

There is a single file called conf which contains the configuration used in
CloudFlare's NGINX servers. This is only a fragment of the configuration.

We currently use OpenSSL 1.0.2-stable (+ patches).


ChaCha20/Poly1305 patch
-----------------------

CloudFlare uses [a patch](https://github.com/cloudflare/sslconfig/tree/master/patches) for
OpenSSL that enables the ChaCha20/Poly1305 cipher suites and implements
special logic to ensure it is only taken if it is the client's top cipher
choice.  Without this patch, the cipher suite choice in the configuration
will not work correctly. This patch is available on the official [cloudflare/sslconfig](https://github.com/cloudflare/sslconfig) or [PPA](https://launchpad.net/~laine-gholson/+archive/ubuntu/chacha-openssl) for Trusty and Xenial on Ubuntu.
