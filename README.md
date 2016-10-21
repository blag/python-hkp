# Python HPK (PGP keyserver) client

## Install

```bash
pip install python-hkp
```

### Usage example:

```python
>>> from hkp import KeyServer
>>> serv = KeyServer('http://pool.sks-keyservers.net')

>>> # Search by name
>>> serv.search('Dmitry Gladkov')
[Key 28DFA7EC RSA (Encrypt or Sign), Key 473C57D9 RSA (Encrypt or Sign)]
>>> serv.search('Dmitry Gladkov')[0].identities
[Identity Dmitry Gladkov (dgl) <dmitry.gladkov@gmail.com>]

>>> # Search by name
>>> serv.search('kclair')
[Key 57D384E3 1, Key 83EB2E0A 1, Key 2795714B 17]
>>> keys = serv.search('kclair')
>>> keys
[Key 57D384E3 1, Key 83EB2E0A 1, Key 2795714B 17]
>>> keys[0].keyid
'57D384E3'
>>> keys[0].key
<key printed here>
>>>
>>> # Fetch a key by keyid
>>> from hkp import Key
>>> hkp_key = Key(host='http://pool.sks-keyservers.net', port=80, keyid='83EB2E0A')
>>> hkp_key.key
<key printed here>

