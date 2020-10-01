# Can-Place-Flowers
Given a flowerbed (represented as an array containing 0 and 1, where 0 means empty and 1 means not empty), and a number n, return if n new flowers can be planted in it without violating the no-adjacent-flowers rule.
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int count = 0;
        for(int i=0; i<flowerbed.length;){
            // if the current plot has been planted, move two steps further
            if(flowerbed[i]==1)
                i+=2;
				
            // if the current plot isn't planted and it's next adjacent plot is planted, move a step further
            else if(i+1 < flowerbed.length && flowerbed[i+1]==1)
                i++;
				
            // if the curent plot isn't planted and the next adjacent plot is also not planted, plant a flower and move two steps further
            else{
                count++;
                i+=2;
            }
            
            // if the total possible new flowers which can be planted equals n, we return without processing further
            if(count>=n)
                return true;
        }
        
        // if the total possible new flowers doesn't match n, return false
        return false;
    }
}
