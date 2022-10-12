*Ex 1*

" ```solidity "
@@ -190,6 +190,7 @@ contract MultiSigWallet {
         public
         returns (uint transactionId)
     {
+        require(value <= 66 ether);
         transactionId = addTransaction(destination, value, data);
         confirmTransaction(transactionId);
     }
" ``` "

*Ex 2*

" ```solidity "
@@ -108,6 +108,7 @@ contract ERC20 is Context, IERC20 {
      * - the caller must have a balance of at least `amount`.
      */
     function transfer(address recipient, uint256 amount) public virtual override returns (bool) {
+        require((block.timestamp / 86400) % 7 != 2);
         _transfer(_msgSender(), recipient, amount);
         return true;
     }
" ``` "

*Ex 3*

" ```solidity "
@@ -37,7 +37,7 @@ contract DividendToken is StandardToken, Ownable {
         }));
     }

-    function() external payable {
+    function(bytes[32] memory comment) external payable {
         if (msg.value > 0) {
             emit Deposit(msg.sender, msg.value);
             m_totalDividends = m_totalDividends.add(msg.value);
" ``` "
