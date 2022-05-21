this is a readme file
func findDisappearedNumbers(nums []int) []int {
    if nums == nil || len(nums) == 0 {
        return nil
    }
    length := len(nums)
    res := make([]int, 0)
    start := 1
    end := length - 1
    for start <= end {
        middle := ((end-start) >> 1) + start
        count := countRange(nums, start, middle)
        if start == end {
            if count > 1 {
                res = append(res, start)
            } else {
                break   
            }
        }
        if count > middle-start+1 {
            end = middle
        } else {
            start = middle+1
        }
    }
    return res
}

func countRange(nums []int, start, end int) int {
    if(nums == nil || len(nums) <= 0) {
        return 0
    }   
    count := 0
    for _, elem := range nums {
        if elem >= start && elem <= end {
            count++
        }
    }
    return count   
}
