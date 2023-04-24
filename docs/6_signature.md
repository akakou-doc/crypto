---
layout: page
title: ディジタル署名方式
nav_order: 6
permalink: /docs/6_signature/
---

# ディジタル署名方式

ディジタル署名方式とは、署名の署名対象が署名者によって送られたか保証する暗号技術である。  
例：合意した契約書（署名対象）がアリス（署名者）から送られてきたものか保証する。  

要はリアル世界で言う「はんこ」のような技術である。  

ディジタル署名方式では、秘密鍵から署名対象に対する署名を生成し、公開鍵を用いてその署名を検証する。

## セキュリティ要件

ディジタル署名方式は、情報の完全性、真正性、否認防止を担保する。

- 完全性
  - 署名対象が改ざんされた場合、署名は検証を通らない
- 真正性
  - 署名者以外は、署名者の有効な署名を生成できない
- 否認防止
  - 署名者は自身の署名を否認できない。


## ディジタル署名の例

- RSA署名
  - RSA暗号がベースとなっている
- ECDSA署名
  - 離散対数問題が解けないことを仮定するディジタル署名
  - ElGamal暗号がベースとなっている
- Schnorr署名
  - 離散対数問題が解けないことを仮定するディジタル署名
  - RSAやECDSAと異なり、暗号方式をベースとしていない。

## RSA署名の仕組み

RSA署名では、RSA暗号を応用することで、ディジタル署名を実現する。  
特にRSA暗号の「平文を暗号化するには、正しい公開鍵が必要な」性質を利用する。

つまりこの「署名の秘密鍵」を「RSAの公開鍵」に、
「署名の公開鍵」を「RSAの秘密鍵」にして、
次のような署名操作と検証操作を実現できる。

- 署名操作
  - 署名の秘密鍵（RSA暗号の公開鍵）で、署名対象を暗号化すること
- 署名検証
  - 署名の公開鍵（RSA暗号の秘密鍵）で暗号を復号し、平文が署名対象か確認すること

<!-- ## ディジタル署名の限界

- 重い  
  **→ハッシュ関数で解決**
- 鍵配送問題
  - 公開鍵が誰のかきちんとわかって、改ざんがされていないことが保証できるのか？  
  **→PKIで解決**
 -->

## ディジタル署名のデモ（RSA）


### 1. 鍵ペアの生成

<iframe src="../demo/rsa_signature_keygen.html" height="350px" width="100%" scrolling="no" frameborder="0"></iframe>

### 2. 署名

<iframe src="../demo/rsa_sign.html" height="350px" width="100%" scrolling="no" frameborder="0"></iframe>

### 3. 検証

<iframe src="../demo/rsa_verify.html" height="350px" width="100%" scrolling="no" frameborder="0"></iframe>