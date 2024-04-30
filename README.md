# Sarai Ayon
# 4/29/24
# CS240 Data Structures and Algorithms
# MergeSort Algorithm

def merge_sort(arr):
    # Base case: if the array has 1 or fewer elements, it is already sorted
    if len(arr) <= 1:
        return arr

    # Divide the array into two halves
    mid = len(arr) // 2
    left_half = arr[:mid]
    right_half = arr[mid:]

    # Recursively sort the left and right halves
    left_half = merge_sort(left_half)
    right_half = merge_sort(right_half)

    # Merge the sorted halves
    return merge(left_half, right_half)

def merge(left, right):
    merged = []
    left_index = 0
    right_index = 0

    # Merge the two halves by comparing elements
    while left_index < len(left) and right_index < len(right):
        if left[left_index] < right[right_index]:
            merged.append(left[left_index])
            left_index += 1
        else:
            merged.append(right[right_index])
            right_index += 1

    # Append any remaining elements from the left and right halves
    merged.extend(left[left_index:])
    merged.extend(right[right_index:])

    return merged

# Example usage:
with open('numbers-4.txt', 'r') as file:
    arr = [int(line.strip()) for line in file]
    sorted_arr = merge_sort(arr)
    print(sorted_arr)

    # Find the position of 90262
    position = sorted_arr.index(90262 )
    print(f"The position of 90262 is {position}")
