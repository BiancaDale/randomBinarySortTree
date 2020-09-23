/**  
  * This program tests whether a random binary sort tree containing 1023 random
  * real numbers is balanced. The program computes the height and the average depth of the tree.
  * If the average depth of the leaves is close to 9 the tree is balanced 
  * @author Bianca Crewe
  * Reference 
  * Eck, D. J. (2019). Introduction to programming using Java, version 8.1. Hobart and William Smith Colleges. http://math.hws.edu/javanotes
  */
public class RandomSortTree {

   static TreeNode root;   // Pointer to the binary sort tree.
   
   /**
    * An object of type TreeNode represents one node in a binary tree of real numbers.
    */
   static class TreeNode {
       double item;      // The data in this node.
       TreeNode left;    // Pointer to left subtree.
       TreeNode right;   // Pointer to right subtree.
       TreeNode(double x) {
              // Constructor.  Make a node containing x.
          item = x;
       }
   } 

   /**
    * TreeInsert method from Eck, D. J. (2019). Introduction to programming using Java, version 8.1. 
    * Hobart and William Smith Colleges. Retrived from http://math.hws.edu/javanotes section 9.4.2. 
    * Add x to the binary sort tree to which the global variable "root" refers.
    */
   static void treeInsert(double x) {
      if ( root == null ) {
              // If the tree is empty set root to point to a new node 
              // containing the new item.
          root = new TreeNode( x );
          return;
       }
       TreeNode runner; // Runs down the tree to find a place for newItem.
       runner = root;   // Start at the root.
       while (true) {
          if ( x < runner.item ) {
                   // Since the new item is less than the item in runner,
                   // it belongs in the left subtree of runner.  If there
                   // is an open space at runner.left, add a node there.
                   // Otherwise, advance runner down one level to the left.
             if ( runner.left == null ) {
                runner.left = new TreeNode( x );
                return;  // New item has been added to the tree.
             }
             else
                runner = runner.left;
          }
          else {
                   // Since the new item is greater than or equal to the 
                   // item in runner, it belongs in the right subtree of
                   // runner.  If there is an open space at runner.right, 
                   // add a new node there.  Otherwise, advance runner
                   // down one level to the right.
             if ( runner.right == null ) {
                runner.right = new TreeNode( x );
                return;  // New item has been added to the tree.
             }
             else
                runner = runner.right;
           }
       } // end while
   }  // end treeInsert()

   /**
    * Return the number of leaves in the tree to which node points.
    */
   static int countLeaves(TreeNode node) {
       if (node == null)
          return 0;
       else if (node.left == null && node.right == null)
          return 1;  // Node is a leaf.
       else
          return countLeaves(node.left) + countLeaves(node.right);
   } // end countNodes()
   
   /**
    * When called as sumOfDepths(root,0), this will compute the
    * sum of the depths of all the leaves in the tree to which root
    * points.  
    * In each recursive call to this routine, depth goes up by one.
    */   
   static int sumOfDepths( TreeNode node, int depth ) {
       if ( node == null ) {
             // Since the tree is empty and there are no leaves,
             // the sum is zero.
          return 0;
       }
       else if ( node.left == null && node.right == null) {
             // The node is a leaf, and there are no subtrees of node, so
             // the sum of the leaf depth is just the depths of this node.
          return depth;
       }
       else {
             // The node is not a leaf.  Return the sum of the
             // the depths of the leaves in the subtrees.
          return sumOfDepths(node.left, depth + 1) 
                      + sumOfDepths(node.right, depth + 1);
       }
   } 
   
   
   /**
    * When called as maximumDepth(root,0), this will compute the
    * max of the depths of all the leaves in the tree to which root
    * points.  
    * In each recursive call to this routine, depth goes up by one.
    */
   static int maximumDepth( TreeNode node, int depth ) {
       if ( node == null ) {
            // The tree is empty.  Return 0.
          return 0;
       }
       else if ( node.left == null && node.right == null) {
             // The node is a leaf, so the maximum depth in this
             // subtree is the depth of this node (the only leaf 
             // that it contains).
          return depth;
       }
       else {
             // Get the maximum depths for the two subtrees of this
             // node.  Return the larger of the two values, which
             // represents the maximum in the tree overall.
          int leftMax = maximumDepth(node.left, depth + 1);
          int rightMax =  maximumDepth(node.right, depth + 1);
          if (leftMax > rightMax)
             return leftMax;
          else
             return rightMax;
       }
   } 
   
   
   /**
    * The main routine makes the random tree and prints the results from the computations.
    */
   public static void main(String[] args) {
         
      root = null;  // Start with an empty tree. 
         
      // Insert 1023 random items into the tree
         
      for (int i = 0; i < 1023; i++)
          treeInsert(Math.random()); 
          
      //  compute and output the average depth of all the leaves in the tree and the maximum depth of all the leaves.
          
      int leafCount = countLeaves(root);
      int depthSum = sumOfDepths(root,0);
      int depthMax = maximumDepth(root,0);
      double averageDepth = ((double)depthSum) / leafCount;
      
      // Display the results.
      
      System.out.println("Number of leaves:  " + leafCount);
      System.out.println("Average depth:  " + averageDepth);
      System.out.println("Maximum depth:  " + depthMax);
   }  

} // end class RandomSortTree
