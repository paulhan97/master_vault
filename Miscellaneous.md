# Ideas

# French
Marc - Gospel of Mark
Commencement - the beginning, the start
le évangile - the gospel
fils - son
Deiu - God
Ésaïe - Isaiah
le prophète - the prophet
messager - messenger
Judée - Judea
Jérusalem - Jerusalem
le fleuve du Jourdain - Jordan River

# Morphological Greek
ΚΑΤΑ ΜΑΡΚΟΝ - According to Mark
Ἀρχὴ - the beginning
τοῦ - definite article (the)
εὐαγγελίου - the gospel
Ἰησοῦ χριστοῦ - Jesus Christ

# Insuresoft's Shenanigans
## 358146 - Policies missing names and addresses
- 4/24/2024, it was identified that some of the data in the `party` and `policy_party_role` tables were not loaded
- Priyanka identified the following as the problem
  - The issue stems from a reload of the `policy` table done in March 2024
  - `Claims_Prestage_Diamond_Load` is set to happen after `Policy_Prestage_Diamond_Load` within the `DTRIC_Daily_Data_Load` job
    - `Claims_Prestage_Diamond_Load` is therefore dependent on the prestage profile tables used in `Policy_Prestage_Diamond_Load`
    - Hence, the data is being truncated when data is missing from the policy profile tables or a few of the transaction tables
- Based on that identification, the proposed solution is to fill in the missing data in the respective profile and transaction tables
- 4/26/2024, filled in missing data for the profile tables. Available for testing
- 4/29/2024, Raj pushes a fix for the address data in the policy transaction tables
- 4/30/2024, David reviewed and verified
- 5/6/2024, Phuoc still found missing names and addresses. Customer testing marked as Verify Failed
- 5/7/2024, Priyanka identified that certain records are not being inserted due to no update in the `last_modified_date`
- 6/5/2024, There are null `party_id`s in the `address` table because `address` is a full load but `policy` and `policyimage` are incremental loads. Therefore, the join is omitting records where data is missing from the incremental loads
- 6/10/2024, Priyanka pushes a fix. This applies also to tickets 357547 and 358202
