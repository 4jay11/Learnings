### Pascal Triangle

Time Complexity : O(numRows^2)

class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> triangle = new ArrayList<>();
        
        // If numRows is 0, return an empty list
        if (numRows == 0) return triangle;
        
        // First row is always1 []
        List<Integer> firstRow = new ArrayList<>();
        firstRow.add(1);
        triangle.add(firstRow);
        
        for (int i = 1; i < numRows; i++) {
            List<Integer> row = new ArrayList<>();
            List<Integer> prevRow = triangle.get(i - 1);
            
            // First element of each row is always 1
            row.add(1);
            
            for (int j = 1; j < i; j++) {
                row.add(prevRow.get(j - 1) + prevRow.get(j));
            }
            
            // Last element of each row is always 1
            row.add(1);
            
            triangle.add(row);
        }
        
        return triangle;
    }
}


Using Formula :

class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> triangle = new ArrayList<>();
        
        for (int i = 0; i < numRows; i++) {
            List<Integer> row = new ArrayList<>();
            long value = 1;
            
            for (int j = 0; j <= i; j++) {
                row.add((int) value);
                value = value * (i - j) / (j + 1);
            }
            
            triangle.add(row);
        }
        
        return triangle;
    }
}

