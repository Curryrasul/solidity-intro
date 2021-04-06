```bash
diff -u ./multisigWallet.sol ./multisigWallet_2.sol
```

```bash
--- multisigWallet.sol	2021-03-19 12:40:00.247999770 +0300
+++ multisigWallet_2.sol	2021-03-19 12:49:20.635997632 +0300
@@ -91,6 +91,11 @@
         _;
     }
 
+    modifier correctValue(uint value) {
+        require(value <= 66 ether);
+        _;
+    }
+
     /// @dev Fallback function allows to deposit ether.
     function()
         payable
@@ -188,6 +193,7 @@
     /// @return Returns transaction ID.
     function submitTransaction(address destination, uint value, bytes data)
         public
+        correctValue(value)
         returns (uint transactionId)
     {
         transactionId = addTransaction(destination, value, data);

```

### Used code : [MultisigWallet](https://github.com/gnosis/MultiSigWallet/blob/master/contracts/MultiSigWallet.sol)
