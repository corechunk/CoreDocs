# 🧩 BitTorrent Wire Protocol Specification

This manual details the BitTorrent peer-to-peer file distribution wire protocol algorithms.

---

## 1. Torrent Metadata & Piece Hashing

Files are split into small fixed-size chunks (e.g., 512KB pieces). The `.torrent` file contains cryptographic SHA-1 hashes for every piece, allowing peers to verify downloaded data integrity independently without central server trust.

---

## 2. Peer Choke/Unchoke Algorithms

Peers exchange TCP messages: `choke`, `unchoke`, `interested`, `have`, `request`, and `piece`. To optimize bandwidth, peers run **Tit-for-Tat** algorithms—unchoking and uploading data to peers that provide the highest reciprocal download rates.
