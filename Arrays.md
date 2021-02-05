### Search in Rotated Sorted Array


public int search(int[] arr, int target) {
        int lo = 0;
        int hi = arr.length-1;
        
        while(lo<=hi){
            int mid = (lo+hi)/2;
            
            if(target==arr[mid]){
                return mid;
            }
            if(arr[lo]<=arr[mid]){
                if(arr[lo]<=target && arr[mid]>target){
                    hi = mid-1;
                }else{
                    lo = mid+1;
                }
            }else if(arr[mid]<arr[hi]){
                if(arr[mid]<target && arr[hi]>=target){
                    lo = mid+1;
                }else{
                    hi = mid-1;
                }
            }
        }
        return -1;
    }
