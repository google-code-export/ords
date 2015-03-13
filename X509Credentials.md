# Introduction #

Secret keys are stored encrypted in the SVN repository. The key is encrypted with a key derived from a 'master' key known only by the virtualisation node using HKDF (see [RFC5869](https://tools.ietf.org/html/rfc5869)). Only derived keys, never the master key, are used to encrypt any data.

Two keys are created for each node with a different 'info' parameter (see [RFC5869](https://tools.ietf.org/html/rfc5869)).
  * `hostkey`: info = host's IP address
  * `vmkey`: info = VM's name

Credentials bound to a specific network address (i.e. certificates used for SSL) are encrypted with the `hostkey`
Credentials assigned to a certain node (i.e. passwords) are encrypted with the `vmkey`

# Details #

X506 certificates are stored in subversion, currently in: `/ords-vmconfig/trunk/hosts/`**`<FQDN>`**`/root/etc/ssl/certs/host-cert.pem`

The matching key is stored here: `/ords-vmconfig/trunk/hosts/`**`<FQDN>`**`/root/etc/ssl/private/host-key.pem.aes-256-cbc`

Use the following command to decrypt / encrypt the private key:

`openssl aes-256-cbc [-d] -a -in inputfile -out outputfile -K key -iv iv`

IVs can be generated using

`od -A n -t x -N 16 /dev/random`