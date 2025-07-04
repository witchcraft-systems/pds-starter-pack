# Setting up a custom did:plc

This guide will help you modify your did:plc so you can point it to a different PDS yourself without losing your identity! ✨

## Obtain secret keys

1. Generate [secret keys using boat](https://boat.kelinci.net/crypto-generate)

    <details>
    <summary>📸 Example image</summary>

    ![Image of using boat.kelinci.net to generate secret keys](/images/secret-keys.png)

    </details>
2. Store these keys in a safe location, for example - in your password manager. (and don't share your private keys with anyone!)

## Add the new keys to your did:plc

1. Open the [PLC applicator](https://boat.kelinci.net/plc-applicator) in boat
2. Enter your handle and password

    <details>
    <summary>📸 Image</summary>

    ![Image of logging into boat.kelinci.net's PLC applicator](/images/apply_plc_login.png)

    </details>
3. Select "Append an operation"

    <details>
    <summary>📸 Image</summary>

    ![Image of selecting "Append an operation" into boat.kelinci.net's PLC applicator](/images/apply_plc_append.png)

    </details>

4. Add your new generated public key (did:key) to the top of the `rotationKeys` array (with a following comma). It is important to add it at the top, since PLC keys aren't all equal, their position in the array defines their priority. If you add it at the bottom, it will not be able to override operations submitted by the old key (which is controlled by your PDS).

    <details>
    <summary>See example payload</summary>

    ```json
    {
      "alsoKnownAs": [
        "at://placeholder.pds.witchcraft.systems"
      ],
      "rotationKeys": [
        "did:key:zQ3shcmcnHahf41czhQHUb4zCLDEaLyHznd1ENHmatUtw6vPn", // add your new public key (did:key) here
        "did:key:zQ3shuT9p9qxyXwJaUPsegQ5GCp7fxyLsjDKS5nybPXSohght" // your old did:key
      ],
      "services": {
        "atproto_pds": {
          "type": "AtprotoPersonalDataServer",
          "endpoint": "https://pds.witchcraft.systems"
        }
      },
      "verificationMethods": {
        "atproto": "did:key:zQ3shrEaHqBf3PtN8r3PksRCRNpiB92czfEZWZUt8DcjExLam"
      }
    }
    ```

    </details>

    <details>
    <summary>📸 Image</summary>

    ![Image of payload data in boat.kelinci.net's PLC applicator](/images/apply_plc_payload.png)

    </details>

5. Request a verification code and enter it below, then press next.

    </details>

    <details>
    <summary>📸 Image</summary>

    ![Image of entering a verification code in boat.kelinci.net's PLC applicator](/images/apply_plc_confirmation.png)

    </details>

    </details>

    <details>
    <summary>Not receiving the email?</summary>

    - Check your junk mail
    - Outlook emails don't seem to work, you can try Proton

    </details>

6. Your did:plc should be updated, which means you can point your did:plc to a different PDS by yourself while keeping your identity!

### See also

- [Identity - AT Protocol](https://atproto.com/guides/identity)
- [DID - AT Protocol](https://atproto.com/specs/did)
- [did-method-plc - GitHub](https://github.com/did-method-plc/did-method-plc)
