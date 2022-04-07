## Key Management Service (KMS)

Managed service that makes it easy for you to create and control your encryption keys.

It is a category within IAM. Although IAM is global, encryption keys are regional.

You cannot export your customer master key.

Permissions are made up of:

- `Key:Administrative`: IAM users/roles that can administer (but not use) it.
- `Key:Usage`: IAM users/roles that can use the key to encrypt/decrypt

Key material options:

- KMS generated
- Your own key

### API

`enable-key-rotation` will rotate the key every year.

Other API calls to know are:

- `aws kms encrypt`
- `aws kms decrypt`
- `aws kms re-encrypt` will decrypt and encrypt again without leaving any trace of the decrypted file

### Envelope Encryption

The master key is used to encrypt/decrypt the envelope key (data key) and that is what is used to encrypt the data.

To decrypt data, we have our encrypted data key, decrypt it with the master key, and use that to decrypt the data itself.
