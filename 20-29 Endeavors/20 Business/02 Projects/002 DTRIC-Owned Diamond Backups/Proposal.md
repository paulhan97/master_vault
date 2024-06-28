# Proposal
[[DTRIC-Owned Diamond Backups]] > Proposal

**Table of Contents**
- [Proposal](#proposal)
  - [Purpose](#purpose)
    - [Having one area where an unrestricted true-copy of Diamond data lives](#having-one-area-where-an-unrestricted-true-copy-of-diamond-data-lives)
    - [Improving the reliability of many potential future options regarding data infrastructure and workflows](#improving-the-reliability-of-many-potential-future-options-regarding-data-infrastructure-and-workflows)
    - [Setting the first domino to having a data lake](#setting-the-first-domino-to-having-a-data-lake)
  - [Questions Posed](#questions-posed)
    - [What difference does it make if Insuresoft owns the storage and not DTRIC?](#what-difference-does-it-make-if-insuresoft-owns-the-storage-and-not-dtric)
    - [How do we ensure that work is not duplicated?](#how-do-we-ensure-that-work-is-not-duplicated)

## Purpose
Given that Insuresoft already has backups of our Diamond production data in their own servers, the issue at-hand is whether DTRIC should own its own copies of Diamond production data. To that end, there are three primary reasons for this proposal:

1. Having one area where an unrestricted true-copy of Diamond data lives
2. Improving the reliability of many potential future options regarding data infrastructure and workflows
3. Setting the first domino to having a data lake

### Having one area where an unrestricted true-copy of Diamond data lives

It is not all that uncommon for SaaS companies to go out-of-business. Therefore, whether it's Insuresoft or any other vendor, we should maintain our own copies of data to prevent the risk of that data being lost due to the servers where the data lives being decomissioned. 

Additionally, if for whatever reason Insuresoft is running into critical issues that leave Diamond in all its versions or the Hub inaccessible/corrupted in some form. We have the fail-safe of knowing that we have our own uncorrupted copies. 

### Improving the reliability of many potential future options regarding data infrastructure and workflows

As it stands, there are several considerations still un-decided:
1. Will DTRIC start development on its own Warehouse?
2. Will Genesys be migrated to Insuresoft's Azure tenancy?
3. Will non-renewal of the Kaboodle contract disrupt any existing data products?

Because all of these big decisions are up in the air, it is unclear what amount of data operations will be best to take internal. However, most of these operations will require DTRIC to have its own copy of Diamond data.

### Setting the first domino to having a data lake
I do not have a good guage on the size of the Diamond data. Regardless of the size, I believe Blob storage is the best candidate for where these backups will be stored. Because that is the case, whatever storage solution we choose can eventually be a data lake. 

In my time here, we have already sunset a few software for which the main obstacle to progress was the users wanting to retain the data. For IT's own purposes, a data lake would make performing the archival of data from un-used software easier. 

## Questions Posed

### What difference does it make if Insuresoft owns the storage and not DTRIC?

My hope is that the section above already answered this question, but because it was a point of contention in the call involving Jim and Kelly. I will dedicate some more to a response. 

If Insuresoft owns the storage, then the water gets muddied if we ever want to consider the storage as a candidate destination for non-Diamond data. If that scenario is possible, then it makes more sense to already have it out of Insuresoft's jurisdiction. 

Additionally, DTRIC will have more control over the storage rules for these backup files (e.g. putting certain backups into colder storage the longer it sits, maintaining multiple past versions of Diamond data at significant junctures, etc.)

### How do we ensure that work is not duplicated?

If I'm not mistaken, this question is only regarding specific work that would happen if the backups get restored and used in some other capacity. Such considerations are beyond the scope of this proposal. 
