$O(n\log n)$ Time Complexity
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        Arrays.sort(nums);
        return nums[nums.length - k];
    }
}
```

$O(n\log n)$ Time Complexity
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
		// priorityqueue sort in ascending order
		// maintain pq of size k, using a minheap
		PriorityQueue<Integer> pq = new PriorityQueue<Integer>();

		// O(n*log(n))
		for(int num : nums) {
			pq.offer(num); // O(log(k))
		}
	
		// O(n)
		// pop off nums.length - k times
		for(int i = 0; i < nums.length - k; i++) {
			pq.poll()
		}

		// O(n*log(n))
		return pq.poll();
	}
}
```