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
2. Go to [bsky.app](https://bsky.app) or [deer.social](https://deer.social/) and select "Create Account".
3. Click on "You are creating an account on Bluesky Social", and set a custom provider URL to `https://pds.witchcraft.systems`.
4. Enter your invite code and the rest of the required information.
5. Congratulations! You now have a PDS account. You may want to subscribe to [@announcements.pds.witchcraft.systems](https://deer.social/profile/announcements.pds.witchcraft.systems) to get updates about the PDS.
6. **Recommended!** [Set up a custom did:plc key](docs/custom-did-plc.md) for your account.

## How to move an existing account to our PDS

1. Get an invite code.
2. You can use [PDSMoover](https://pdsmoover.com) (recommended) or the [ATP INTERNECTIONAL AIRPORT](https://atpairport.com/)(alpha) for a more user-friendly experience. If you're comfortable with a terminal - you can also follow [this guide](https://whtwnd.com/bnewbold.net/entries/Migrating%20PDS%20Account%20with%20%60goat%60) to migrate using the `goat` tool.

Keep in mind that those tools are made for did:plc; If you have a did:web - good luck, you figured it out when you created the account, so surely you'll figure it out now too :^) (if you don't know which one you have - don't worry about it, you probably have a did:plc).

>[!TIP]
> If you get an error when using the automatic Goat migration or ATP methods, please check this [doc](docs/plcfix.md)
3. Done!
4. **Recommended if using did:plc!** [Set up a custom did:plc key](docs/custom-did-plc.md) for your account.

## How to leave if we ever go down

We have no plans of shutting down the PDS, but for your benefit, here are the rough steps to migrate your data to another PDS if we ever do:

0. Have [custom keys in your did:plc](docs/custom-did-plc.md) or use a did:web.
1. Grab the files for your DID from the [nightly backups S3 bucket](https://link.storjshare.io/s/jufla747mctifdglkggg2jqhvddq/pds-witchcraft-systems/backups/).
2. Upload the CAR contents and the blobs to your new PDS.
3. Point your DID at the new PDS.
4. Update your handle if it was a subdomain of `pds.witchcraft.systems`.
