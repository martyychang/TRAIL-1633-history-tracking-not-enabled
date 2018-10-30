# SFDX  App

This repo demonstrates a bug with Salesforce DX observed in Winter '19
and API 44.0, regarding the ability to push source to new scratch orgs
with field history tracking enabled

## Dev, Build and Test

1. Clone this repo
2. Create a new scratch org using **config/project-scratch-def.json**
3. Push source to the new scratch org using `sfdx force:source:push`.
   An error, "Account does not have history tracking enabled' will be reported.
4. Push source again by repeating the exact same `sfdx force:source:push`
   command from the previous step

At this point, no errors are reported. Furthermore, running `sfdx force:org:open` to inspect the org reveals that field history tracking is _still_ disabled for the Account object, despite no errors having been reported from the most recent `force:source:push` command.

Below are two unmet expectations.

* No errors should be raised on the first `force:source:push` command
* Account field history tracking should be enabled when no errors are reported
  from a `force:source:push` command

## Resources

* "[Push Source to the Scratch Org][1]." _Salesforce DX Developer Guide_.

[1]: https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_push_md_to_scratch_org.htm
