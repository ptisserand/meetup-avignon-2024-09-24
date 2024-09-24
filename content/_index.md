+++
title = "2024-09-24 Meetup"
outputs = ["Reveal"]

+++

# Intro cryptographie & blockchain

Meetup Avignon 2024-09-24

---

## La cryptographie?

- Confidentialité: chiffrement
- Intégrité: hachage
- Authenticité: signature

---

### Principaux types de chiffrement

- Symétrique
- Asymétrique
- Hybride

---
### Chiffrement symétrique
- Secret partagé: la clé de chiffrement
- e(data, PrivK) => ciphered
- d(ciphered, PrivK) => data
- Rapide
- Difficulté pour le partage du secret
- AES

--- 
### Chiffrement asymétrique
- Clé privée et clé publique
- e(data, PubK) => ciphered
- d(ciphered, PrivK) => data
- Plus lent
- RSA

---
### Chiffrement hybride
- Partage du secret via chiffrement asymétrique
- Chiffrement symétrique ensuite
- Protocole Diffie-Hellman
- HTTPS (HTTP over TLS)

---
### Hachage
- Empreinte "digitale" de taille fixe
- h(data) => fingerprint
- Non réversible
- Petite modification des données donne une empreinte totalement différente
- SHA256 / SHA1 (git)

---
### Signature
- s(data, PrivK) => signature
- v(data, signature, PubK) => OK/KO
- RSA, DSA, ECDSA

---
## Blockchain
- Stockage et transmission d'information
- Le bloc suivant référence le précédent (hash)
- Mono branche / multi branches
- Utilisation dans git
- 1 bloc contient plusieurs transactions

---
### Blockchain décentralisée: Consensus
- Accord des noeuds du réseau pour l'état d'une blockchain
- Désaccord => Fork
- POW (Bitcoin)
- POS (Ethereum)

--- 
### Proof of Work: mineurs
- Concurrence entre les mineurs pour trouver le prochain bloc
- Puissance nécessaire pour résoudre le calcul
- Vérification moins couteuse
- Forte consommation électrique

---
### Proof of Stake: validateurs
- Dépot par les validateurs
- Sélection aléatoire (pondérée) d'un validateur
- Faible consommation électrique
- Malveillance => Perte partielle du dépôt 

---
### Transaction Bitcoin
- Envoi et/ou transfert de valeur entre 2 parties
- Entrées: origine des actifs
- Sorties: destination des actifs
- Signature de la transaction
- UTXO: Unspend Transaction Output
- Bitcoin script défini la contrainte sur l'utilisation d'un actif

---
### Bitcoin script
- Utilisation d'une pile (stack)
- Limitation des possibilités
- Ensemble d'opcodes
```
OP_DUP OP_HASH160 b2089ebaad05c87a6d714cc33fbaa8cf181a4e30
OP_EQUALVERIFY OP_CHECKSIG
```
- BIP

---
### Transaction Ethereum
- Modification d'état de smart contracts
- Signature de la transaction
- EVM: Machine virtuelle Ethereum

---
### EVM 
- Utilisation d'une pile et d'une mémoire
- Ensemble d'opcodes
- Compilation
- Langages: Solidity, Vyper, Yul (assembleur)
- EIP: ERC20, ERC721

---
### Solidity
```solidity
// SPDX-License-Identifier: MIT
// Compatible with OpenZeppelin Contracts ^5.0.0
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is ERC20, Ownable {
    constructor(address initialOwner)
        ERC20("MyToken", "MTK")
        Ownable(initialOwner)
    {}

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }
}
```

---
## Questions ?

https://github.com/ptisserand
p.tisserand@cacango.com
