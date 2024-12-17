# passwords
A small set of functions to help with password handling in APL-based systems. In a nutshell:

1) Generate random "salt" for each user
2) Compute the hash of the combination of salt + user password

We store the salt and the hash for each user and use it to validate passwords. 
The key benefits of this approach are:

1) We do not store passwords
2) Two users who have the same password will have different hashes due to the random salt

The function `NewGuid` to generate Globally Unique Identifiers (GUIDs) is also included. This is
not directly related to password validation, but useful in assigning unique IDs to 
user sessions.

# Public API
|Syntax|Description|
|-|-|
|`Init`|Randomise RNG seed and initialise Hash/Guid generators|
|`(salt hash)←SaltAndHash pwd`|Generate salt and compute hash for a new password|
|`NewGuid`|Return a GUID|

# Subfunctions - Not intended for pblic use
|Syntax|Description|
|-|-|
|`hash←hash salt text`|Generate hash|
|`salt←makeSalt n`|Generate n random 16-element character vectors suitable as salt|
|`SHA256.ComputeHash`|Compute a SHA256 hash of a character vector|

