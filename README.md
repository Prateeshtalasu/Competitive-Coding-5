# Competitive-Coding-5

Please submit the interview problems posted in slack channel here. The problems and statements are intentionally not shown here so that students are not able to see them in advance 
class Solution {
    public List<Integer> largestValues(TreeNode root) {
         
        Queue<TreeNode> q = new LinkedList<>();
        List <Integer> result = new ArrayList<>();
        if (root == null) { // Handle the case where root is null
            return result;
        }
        q.add(root);
        while(!q.isEmpty()){
            int size = q.size();
              int max = Integer.MIN_VALUE;
            for(int i=0 ;i<size;i++){
                TreeNode current = q.poll();
                max = Math.max(max,current.val);
                if(current.left!=null){
                    q.add(current.left);
                }
                 if(current.right!=null){
                    q.add(current.right);
                }
            }
            result.add(max);
            

        }
        return result;
    }
}
//
class Solution {
    public boolean isValidSudoku(char[][] board) {
       Set <Character> [] rows = new HashSet [9];
       Set <Character> [] cols = new HashSet [9];
       Set <Character> [] boxes = new HashSet [9];

        for (int i = 0; i < 9; i++) {
            rows[i] = new HashSet<>();
            cols[i] = new HashSet<>();
            boxes[i] = new HashSet<>();
        }

       for(int r=0;r<9;r++){
        for(int c=0;c<9;c++){
            char val = board[r][c];
            if(val== '.') continue;

            int boxindex = (r/3) *3+c/3;
            // (r / 3) * 3 counts how many full box rows we’ve passed (each row has 3 boxes),
                // and (c / 3) counts how many boxes into the current row we are.
                // Together, they give a unique index for each of the 9 boxes in a 3x3 layout.
            if(rows[r].contains(val)) return false;
            if(cols[c].contains(val)) return false;
            if(boxes[boxindex].contains(val)) return false;

            rows[r].add(val);
                cols[c].add(val);
                boxes[boxindex].add(val);
        }
     
       }

   return true;
    }
}
