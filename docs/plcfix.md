# Weird PLC bug in auto migration fix:
So, you tried to migrate your account to a custom PDS automatically but something broke?

Example error:
> error: failed importing repo: request failed: Post "https://pds.witchcraft.systems/xrpc/com.atproto.repo.importRepo": POST pds.witchcraft.systems/xrpc/com.atp... giving up after 1 attempt(s): context deadline exceeded (Client.Timeout exceeded while awaiting headers)

## Why this happens:
When migrating an account, the program has to request a PLC token to transfer over your DID (Your identity that actually points to where your account is stored). That token has a lifespan for security reasons, around 10 minutes if I remember correctly. However, when migrating particularly __beefy__ accounts it may take a while to transfer your records and blobs to the new pds and by the time all the stuff is transferred, the PLC token runs out.

## The fix:

If i understand how it works correctly, all the blobs and records should be transferred fine, so the only thing we need to fix is the PLC identity not pointing to the right place

The following section is mostly copied from the [The Guide's](https://whtwnd.com/bnewbold.net/entries/Migrating%20PDS%20Account%20with%20%60goat%60) manual migration section.

First, install [Goat](https://github.com/bluesky-social/goat) (If you were migrating through goat in the first place, you may obviously skip this step)

> To login to the account on a specific PDS: 
>
> `goat account login -u YOUR_USERNAME -p YOUR_PASSWORD --pds-host PDS_HOST`
>
> To find out your PDS_HOST for the bluesky-hosted account, you can use [pdsls](pdsls.dev) or any similar tool.

1. Check the status of the new account:
	```
	# new PDS
	goat account status
	```
	If the repo and blob count seem fine, you can continue


2. Get the PLC settings from the new PDS
	```
	# new PDS
	goat account plc recommended > plc_recommended.json
	```

3. Get a PLC token from the old PDS
	```
	# old PDS
	goat account plc request-token
	```

4. Sign your plc settings with the token

	```
	# old PDS
	goat account plc sign --token $PLCTOKEN  ./plc_recommended.json > plc_signed.json
	```

5. Submit the PLC operation from the new PDS
	```
	# new PDS
	goat account plc submit ./plc_signed.json
	```
6. Deactivate the old account and activate the new
	```
	# old PDS
	goat account deactivate
	# new PDS
	goat account activate
	```

That should be it, hopefully, if not, you know who to bother for help