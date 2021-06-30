Create a new Scratch Org
`sfdx force:org:create -a rtTest -f ./config/project-scratch-def.json`

Deploy to Account to Enable History Tracking
`sfdx force:mdapi:deploy -u rtTest -d pre-test -w 15`

Deploy to Account again to add a Record Type
`sfdx force:mdapi:deploy -u rtTest -d test -w 15`

Results in the error

> === Component Failures [1]
>
> TYPE FILE NAME PROBLEM
>
> ───── ─────────────────────────── ─────── ───────────────────────────────────────────────────────────────────────────────
>
> Error test/objects/Account.object Account Custom Field Definition ID: bad value for restricted picklist field: RecordType

Once you confirm the problem occurs then you can deploy test-fix-1 and test-fix-2 which breaks up the deployments to add the Record Type in a deployment before trying to add history tracking for it.

Deploy to Account again to add a Record Type
`sfdx force:mdapi:deploy -u rtTest -d test-fix-1 -w 15`

Deploy to Account again to add a Record Type
`sfdx force:mdapi:deploy -u rtTest -d test-fix-2 -w 15`

Which has the same outcome as what should happen if the `test` deployment were successful.
