# Security Considerations

The IoTeX DID method covers both people and devices and the following security issues are considered:

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#private-key-compromise)Private Key Compromise <a id="private-key-compromise"></a>

The ownership of DIDs is solely based on the knowledge of private keys. Hence the secure storage of private keys is critical. To minimize the risk of private key compromise, using security hardware for key storage is highly recommended. Furthermore, in the case that private key is lost or stolen, an identifier recovery mechanism needs to be in place for enabling a legitimate entity to regain control of the identifier.

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#replay-and-impersonation-attacks)Replay and Impersonation Attacks <a id="replay-and-impersonation-attacks"></a>

A malicious service provider might collect credentials of people and devices with the purpose of impersonating other legitimate entities to gain access for certain services. This issue can be addressed by service providers conducting a challenge-response process with the request entities, thereby verifying that a DID is associated with the request entity.

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#integrity-of-did-documents-and-credentials)Integrity of DID Documents and Credentials <a id="integrity-of-did-documents-and-credentials"></a>

The IoTeX DID method allows people and devices to store the DID documents and credentials in the storage of their choices. The integrity of this information is ensured by the IoTeX blockchain.

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#denial-of-service-attacks)Denial of Service Attacks <a id="denial-of-service-attacks"></a>

An attacker might launch the Denial of Service \(DoS\) attacks to prevent access of certain DID documents and/or credentials. To mitigate this issue, DID owners may deploy data redundancy countermeasures by storing multiple copies of DID documents and/or credentials in different storage locations.

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#smart-contract-flaws)Smart Contract Flaws <a id="smart-contract-flaws"></a>

The IoTeX DIDs method is implemented by smart contracts on the IoTeX blockchain. Those contracts will go through stringent audits and tests to mitigate the potential security risks.

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#quantum-computer-threats)Quantum Computer Threats <a id="quantum-computer-threats"></a>

The private/public key pair used in IoTeX DID method is based on elliptic curve cryptosystems \(ECC\). The future occurrence of powerful quantum computers will render ECC insecure. Under such a circumstance, a key updating mechanism is needed to generate a new key pair based on the post-quantum cryptographic algorithm selected by the National Institute of Standards and Technology \(NIST\) for replacing the old one.

### [\#](https://docs.iotex.io/developer/did/security-notes.html#privacy-considerations)Privacy Considerations <a id="privacy-considerations"></a>

The IoTeX DID method involves privacy protection for people and devices and the following privacy issues are considered:

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#private-data-leakage)Private Data Leakage <a id="private-data-leakage"></a>

When a person shares his/her personal information with a service provider, the service provider might leak the data to third parties without users’ consent. This issue can be minimized by only sharing the necessary data during the interaction with the service provider rather than exposing the full credential. Advanced cryptographic techniques such as zero-knowledge proofs might be employed to address this issue under certain circumstances.

#### [\#](https://docs.iotex.io/developer/did/security-notes.html#people-device-tracking)People/Device Tracking <a id="people-device-tracking"></a>

Since IoTeX DIDs are managed by smart contracts and all the interactions with the smart contracts are recorded on the IoTeX blockchain. By analyzing the transactions on the blockchain, attackers might be able to review the interaction patterns among people or between people and devices. This issue can be minimized by constantly altering the DIDs of people and devices for different interactions according to a predefined policy.

