# Max heap implementation
# By default,heapq is min heap. Multiply ele by -1 to get max heap

from heapq import heapify,heappush,heappop

heap = []
heapify(heap)

heappush(heap,-1*10)
heappush(heap,-1*20)
heappush(heap,-1*30)
heappush(heap,-1*40)

for i in heap:
    print(-i)

heappop(heap)
print("")
for i in heap:
    print(-i)

---
# kth smallest element(Max heap)

from heapq import heapify,heappush,heappop

def k_sm(arr,k):                                    ### T.C.:- O(NlogK)
    heap = []                                       ### S.C.:- O(K)
    heapify(heap)
    for i in arr:
        heappush(heap,-i)
        if len(heap)>k:
            heappop(heap)
    return -heappop(heap)
    
arr = list(map(int,input().split()))
k = int(input())
print(k_sm(arr,k))

# kth largest element(Min heap)

from heapq import heapify,heappush,heappop

def k_sm(arr,k):
    heap = []                                      ### T.C.:- O(NlogK)
    heapify(heap)                                  ### S.C.:- O(K)
    for i in arr:
        heappush(heap,i)
        if len(heap)>k:
            heappop(heap)
    return heappop(heap)
    
arr = list(map(int,input().split()))
k = int(input())
print(k_sm(arr,k))

# K largest elements(Min heap)

from heapq import heapify,heappush,heappop

def k_sm(arr,k):
    heap = []                                      ### T.C.:- O(NlogK)
    heapify(heap)                                  ### S.C.:- O(K)
    for i in arr:
        heappush(heap,i)
        if len(heap)>k:
            heappop(heap)
    return heap
    
arr = list(map(int,input().split()))
k = int(input())
ans = k_sm(arr,k)
print(*ans)

# Sort a K Sorted Array(Nearly Sorted)(Min heap)

from heapq import heapify,heappush,heappop

def nearly_sorted(arr,k):
    heap = []
    heapify(heap)                                          ### T.C.:- O(NlogK)
    ans = []                                               ### S.C.:- O(K)
    for i in arr:
        heappush(heap,i)
        if len(heap)>k:
            ans.append(heappop(heap))
    while(len(heap)>0):
        ans.append(heappop(heap))
    return ans
    
arr = list(map(int,input().split()))
k = int(input())
ans = nearly_sorted(arr,k)
print(*ans)

# K Closest Numbers(Max heap)

from heapq import heapify,heappush,heappop

def k_closest(arr,k,x):
    heap = []
    heapify(heap)
    for i in arr:
        heappush(heap,[-abs(i-x),i])                        ### T.C.:- O(NlogK)  Sorting based on first value of pair
        if len(heap)>k:                                     ### S.C.:- O(K)      Absolute Diff is used as a key
            heappop(heap)
    ans = []
    while(len(heap)>0):
        j = heappop(heap)
        ans.append(j[1])
    return ans
    
arr = list(map(int,input().split()))
k = int(input())
x = int(input())
ans = k_closest(arr,k,x)
print(*ans)

# Top K Frequent Numbers(Min heap)

def topKFrequent(nums,k):
    d = dict()
    for i in nums:                             ### T.C.:- O(NlogK)
        if i in d:                             ### S.C.:- O(K)
            d[i]+=1
        else:
            d[i] = 1
    heap = []
    heapify(heap)
    for i in d.keys():
        heappush(heap,[d[i],i])                # Frequency is used as a key
        if len(heap)>k:
            heappop(heap)
    ans = []
    while(len(heap)>0):
        j = heappop(heap)
        ans.append(j[1])
    return ans

nums = list(map(int,input().split()))
k = int(input())
ans = topKFrequent(nums,k)
print(*ans)

# Frequency Sort(Max heap)

from heapq import heapify,heappush,heappop

def freq_sort(arr):
    d = dict()
    for i in arr:                          ### T.C.:- O(NlogK)
        if i in d:                         ### S.C.:- O(K)
            d[i]+=1
        else:
            d[i] = 1
    heap = []
    heapify(heap)
    for i in d.keys():
        heappush(heap,[-d[i],i])
    ans = []
    while(len(heap)>0):
        j = heappop(heap)
        f = -j[0]
        ele = j[1]
        for i in range(f):
            ans.append(ele)
    return ans
    
arr = list(map(int,input().split()))
ans = freq_sort(arr)
print(*ans)



