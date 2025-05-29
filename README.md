# Witchcraft Systems Personal Data Sanctum

## Links

- [PDS itself](https://pds.witchcraft.systems)
- [Uptime status page](https://stats.uptimerobot.com/7Xeatuzb2h)
- [Witchcraft Systems main account](https://deer.social/profile/did:web:witchcraft.systems)
- [Witchcraft Systems infrastructure issues account](https://deer.social/profile/did:plc:ebwglxznjtpxr4ybttbpbwjw) (hosted on a Bluesky PBC PDS, used if our infrastructure is down)
- [Witchcraft Systems PDS announcements account](https://pds.witchcraft.systems/profile/) (used for reporting issues with the PDS)
- [This repository](https://git.witchcraft.systems/scientific-witchery/pds-starter-pack) and the [github mirror](https://github.com/witchcraft-systems/pds-starter-pack)
- [PDS nightly backups](https://link.storjshare.io/s/jufla747mctifdglkggg2jqhvddq/pds-witchcraft-systems/backups/)

## How to sign up

1. Get an invite code from one of the designated witches.
2. Go to [bsky.app](https://bsky.app) and select "Create Account".
3. Click on "You are creating an account on Bluesky Social", and set a custom provider URL to `https://pds.witchcraft.systems`.
4. Enter your invite code and the rest of the required information.
5. Congratulations! You now have a PDS account.

## How to leave if we ever go down

We have no plans of shutting down the PDS, but for your benefit, here are the rough steps to migrate your data to another PDS if we ever do:

0. Have custom keys in your did:plc or use a did:web.
1. Grab the files for your DID from the [nightly backups S3 bucket](https://link.storjshare.io/s/jufla747mctifdglkggg2jqhvddq/pds-witchcraft-systems/backups/).
2. Upload the CAR contents and the blobs to your new PDS.
3. Point your DID at the new PDS.
4. Update your handle if it was a subdomain of `pds.witchcraft.systems`.
