# Witchcraft Systems Personal Data Sanctum

## Links

- [PDS itself](https://pds.witchcraft.systems)
- [Uptime status page](https://stats.uptimerobot.com/7Xeatuzb2h)
- [Witchcraft Systems main account](https://deer.social/profile/did:web:witchcraft.systems)
- [Infrastructure issues account](https://deer.social/profile/did:plc:ebwglxznjtpxr4ybttbpbwjw) (hosted on a Bluesky PBC PDS, used if our infrastructure is down)
- [PDS announcements account](https://deer.social/profile/announcements.pds.witchcraft.systems) (used for stuff that's only relevant to those who use our PDS)
- [This repository](https://git.witchcraft.systems/scientific-witchery/pds-starter-pack) and the [github mirror](https://github.com/witchcraft-systems/pds-starter-pack)
- [PDS nightly backups](https://link.storjshare.io/s/jufla747mctifdglkggg2jqhvddq/pds-witchcraft-systems/backups/)

## About the PDS

This is a Personal Data Sanctum (PDS) hosted by Witchcraft Systems, physically located in Tokyo, Japan. Signups require an invite code, which can be obtained by sending a message to us on our [main account](https://deer.social/profile/did:web:witchcraft.systems).

While you can move your main account to our PDS, we do not recommend doing so if you don't have an alternative option just in case (i.e. you use a Bluesky PBC PDS, since moving your main account to a custom PDS makes it impossible to move it back to a PDS hosted by the Bluesky PBC).

The PDS is operated on a best-effort basis, meaning we will try to keep it up and running, but we cannot guarantee 100% uptime. You can check our uptime so far on our [status page](https://stats.uptimerobot.com/7Xeatuzb2h) and decide if this is acceptable for you.

The PDS itself is backed up nightly to multiple locations, with the backups being regularly verified to ensure data integrity. All the public data stored on the PDS is also available in an [S3 bucket](https://link.storjshare.io/s/jufla747mctifdglkggg2jqhvddq/pds-witchcraft-systems/backups/), which will continue to be available even if the PDS itself goes down, and can be used to migrate your account to another PDS if needed.

In case of anything significant affecting the PDS, we will do our best to tell you about it on our [PDS announcements account](https://deer.social/profile/announcements.pds.witchcraft.systems), in advance where possible.

## How to sign up

1. Get an invite code.
2. Go to [bsky.app](https://bsky.app) or [deer.social](https://https://deer.social/) and select "Create Account".
3. Click on "You are creating an account on Bluesky Social", and set a custom provider URL to `https://pds.witchcraft.systems`.
4. Enter your invite code and the rest of the required information.
5. Congratulations! You now have a PDS account. You may want to subscribe to [@announcements.pds.witchcraft.systems](https://deer.social/profile/announcements.pds.witchcraft.systems) to get updates about the PDS.
6. **Recommended!** [Set up a custom did:plc key](#setting-up-a-custom-didplc) for your account. You can use [boat](https://boat.kelinci.net/) to both generate a key pair (store it somewhere safe!) and to add the public key to your account. This will allow you to point your DID to a different PDS without using our PDS's key.

## How to move an existing account to our PDS

0. Remember that migrating from the default Bluesky PDS to a custom PDS is a one-way operation.
1. Get an invite code.
2. Follow [this guide](https://whtwnd.com/bnewbold.net/entries/Migrating%20PDS%20Account%20with%20%60goat%60) to migrate using the `goat` tool. Otherwise, you can use the [ATP INTERNECTIONAL AIRPORT](https://atpairport.com/) for a more user-friendly experience, but it is currently in alpha and may not work as expected. Keep in mind that those tools are made for did:plc; If you have a did:web - good luck, you figured it out when you created the account, so surely you'll figure it out now too :^)
3. Done!
4. **Recommended if using did:plc!** [Set up a custom did:plc key](#setting-up-a-custom-didplc) for your account. You can use [boat](https://boat.kelinci.net/) to both generate a key pair (store it somewhere safe!) and to add the public key to your account. This will allow you to point your DID to a different PDS without using our PDS's key.

### Setting up a custom did:plc

#### Obtain secret keys

1. Generate [secret keys using boat](https://boat.kelinci.net/crypto-generate)

    <details>
    <summary>📸 Image</summary>

    ![Image of using boat.kelinci.net to generate secret keys](/images/secret-keys.png)

    </details>
2. Store these keys in a safe location! (and don't share your private keys with anyone!)

#### Add the new keys to your did:plc

1. Open the [PLC applicator](https://boat.kelinci.net/plc-applicator)
2. Enter your handle and login

    <details>
    <summary>📸 Image</summary>

    ![Image of logging into boat.kelinci.net's PLC applicator](/images/apply_plc_login.png)

    </details>
3. Select "Append an operation"

    <details>
    <summary>📸 Image</summary>

    ![Image of selecting "Append an operation" into boat.kelinci.net's PLC applicator](/images/apply_plc_append.png)

    </details>

4. Add your new generated public key (did:key) to the top of the `rotationKeys` array (with a following comma)

    <details>
    <summary>See example payload</summary>

    ```json
    {
      "alsoKnownAs": [
        "at://placeholder.pds.witchcraft.systems"
      ],
      "rotationKeys": [
        "did:key:zQ3shcmcnHahf41czhQHUb4zCLDEaLyHznd1ENHmatUtw6vPn", // your new public key (did:key)
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

## How to leave if we ever go down

We have no plans of shutting down the PDS, but for your benefit, here are the rough steps to migrate your data to another PDS if we ever do:

0. Have [custom keys in your did:plc](#setting-up-a-custom-didplc) or use a did:web.
1. Grab the files for your DID from the [nightly backups S3 bucket](https://link.storjshare.io/s/jufla747mctifdglkggg2jqhvddq/pds-witchcraft-systems/backups/).
2. Upload the CAR contents and the blobs to your new PDS.
3. Point your DID at the new PDS.
4. Update your handle if it was a subdomain of `pds.witchcraft.systems`.
