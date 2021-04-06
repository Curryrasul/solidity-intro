```bash
diff -u ./dividendToken.sol ./dividendToken_2.sol
```

```bash
--- dividendToken.sol	2021-03-19 11:04:26.787998305 +0300
+++ dividendToken_2.sol	2021-03-19 12:28:31.391992789 +0300
@@ -37,10 +37,11 @@
         }));
     }
 
-    function() external payable {
+    function deposit(bytes32 _comment) external payable {
         if (msg.value > 0) {
             emit Deposit(msg.sender, msg.value);
             m_totalDividends = m_totalDividends.add(msg.value);
+            comment = _comment;
         }
     }
 
@@ -163,6 +164,11 @@
         return 1000;
     }
 
+    // Get comment from deposit()
+    function getComment() external view returns (byte32) {
+        return comment;
+    }
+
     /// @notice record of issued dividend emissions
     EmissionInfo[] public m_emissions;
 
@@ -175,4 +181,6 @@
 
     uint256 public m_totalHangingDividends;
     uint256 public m_totalDividends;
+
+    bytes32 private comment;
 }

```

### Used code : [DividendToken](https://github.com/mixbytes/solidity/blob/076551041c420b355ebab40c24442ccc7be7a14a/contracts/token/DividendToken.sol)
