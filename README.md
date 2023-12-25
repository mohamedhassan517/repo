import java.util.Arrays;
class Solution {
    public int linearSearch(int[] nums, int value){
        for(int i = 0; i < nums.length; i++){
            if(nums[i] == value) return i;
        }
        return -1;
    }
    public int linearSearch(int[] nums, int value, int found){
        for(int i = 0; i < nums.length; i++){
            if(found != i && nums[i] == value) return i;
        }
        return -1;
    }
    public int[] twoSum(int[] nums, int target) {
        int result[] = {0,0};
        int[] numsCpy = Arrays.copyOf(nums, nums.length);
        Arrays.sort(numsCpy);
        for(int i = 0; i < nums.length - 1; i++){
            if(numsCpy[i] < target - numsCpy[numsCpy.length - 1]) continue;
            else if(numsCpy[i] == target - numsCpy[numsCpy.length - 1]){
                result[0] = linearSearch(nums, numsCpy[i]);
                result[1] = linearSearch(nums, numsCpy[numsCpy.length - 1], result[0]);
            }else{
                for(int j = i + 1; j < numsCpy.length - 1; j++){
                    if(numsCpy[i] == target - numsCpy[j]){
                        result[0] = linearSearch(nums, numsCpy[i]);
                        result[1] = linearSearch(nums, numsCpy[j], result[0]);
                        break;
                    }
                }
            }
        }
        return result;
    }
}
