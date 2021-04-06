```bash
diff -u ./erc20.sol ./erc20_2.sol
```

```bash
--- erc20.sol	2021-03-14 23:19:36.116233281 +0300
+++ erc20_2.sol	2021-03-17 21:20:02.403983889 +0300
@@ -206,6 +206,12 @@
      * - `sender` must have a balance of at least `amount`.
      */
     function _transfer(address sender, address recipient, uint256 amount) internal virtual {
+        // // 0 - Sunday, 1 - Monday, ..., 6 - Saturday.
+        uint256 dayOfAWeek = (block.timestamp / 86400 + 4) % 7;
+
+        // Prevent a transfer on Saturday
+        require(dayOfAWeek != 6, "Forbidden on Saturdays");
+        
         require(sender != address(0), "ERC20: transfer from the zero address");
         require(recipient != address(0), "ERC20: transfer to the zero address");
```

### Used code : [ERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/f2112be4d8e2b8798f789b948f2a7625b2350fe7/contracts/token/ERC20/ERC20.sol)
