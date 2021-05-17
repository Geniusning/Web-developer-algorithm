```
//1.两数之和
//暴力解法
function twoSum (nums, target) {
  for (let i = 0; i < nums.length; i++) {
    let other = target - nums[i]
    for (let j = i + 1; j < nums.length; j++) {
      if (other === nums[j]) {
        return [i, j]
      }
    }
  }
}
// console.log(mapTwosum([3,3],6))

function mapTwosum (nums, target) {
  let map = new Map()
  for (let i = 0; i < nums.length; i++) {
    let other = target - nums[i]
    if (map.get(other) != undefined) {
      return [map.get(other), i]
    }
    map.set(other, i)
  }
  return false
}

//7 整数反转
// console.log(reverseNum(1230))
function reverseNum (x) {
  let res = 0
  while (x) {
    res = res * 10 + x % 10
    if (res > Math.pow(2, 31) - 1 || res < Math.pow(-2, 31)) return 0
    x = ~~(x / 10)
  }
  return res
}

//9.回文数
function isPalindrome (nums) {
  nums = nums.toString()
  console.log(nums)
  let i = 0, j = nums.length - 1
  while (i < j) {
    if (nums[i] != nums[j]) {
      return false
    }
    i++
    j--
  }
  return true
}
function isPalindrome1 (n) {
  if (n < 0) {
    return false
  }
  let res = 0
  let num = n
  while (num) {
    res = res * 10 + num % 10
    num = ~~(num / 10)
  }
  return res === n
}
// console.log(isPalindrome1(122321))

//13.罗马数字转整数
function roman2Int (num) {
  let hasNum = {
    "I": 1,
    "V": 5,
    "X": 10,
    "L": 50,
    "C": 100,
    "D": 500,
    "M": 1000,
  }
  let res = 0
  for (let i = 0, len = num.length; i < len; i++) {
    hasNum[num[i]] < hasNum[num[i + 1]] ? res -= hasNum[num[i]] : res += hasNum[num[i]]
  }
  return res
}
// console.log(roman2Int("LVIII"))

function longestCommonPrefix (strArr) {
  if (strArr.length === 1) {
    return strArr[0]
  }
  if (strArr.length === 0) {
    return ""
  }
  let firstStr = strArr[0]
  for (let i = 0; i < firstStr.length; i++) {
    for (let s of strArr) {
      if (s[i] !== firstStr[i]) return s.slice(0, i)
    }
  }
  return strArr[0]
  //   // let firstStr = strArr[0]
  //   // let res = ""
  //   // console.log("firstStr",firstStr)
  //   // for (let i = 0;i < firstStr.length;i++) {
  //   //   let flag = strArr.every(item=> item[i] === firstStr[i])
  //   //   if (flag) {
  //   //     res += firstStr[i]
  //   //   }else {
  //   //     return res
  //   //   }
  //   // }
  //   // return res
  // }
}
let arr = ["flower", "f2low", "afaflight"]
// console.log(longestCommonPrefix(arr))

//有效的括号 (([]))
function isValid (s) {
  let map = new Map([["]", "["], ["}", "{"], [")", "("]])
  let stack = []
  let flag = true
  for (let i = 0; i < s.length; i++) {
    if (!map.has(s[i])) {
      stack.push(s[i])
    } else if (map.has(s[i]) && map.get(s[i]) === stack.pop()) {
      flag = true
    } else {
      return false
    }
  }
  if (stack.length !== 0) return false
  return flag
}
console.log(isValid("([)]"))

//21.合并两个有序列表
function mergeTwoList (l1, l2) {
  if (l1 === null) {
    return l2
  }
  if (l2 === null) {
    return l1
  }

  if (l1.val < l2.val) {
    l1.next = mergeTwoList(l1.next, l2)
    return l1
  } else {
    l2.next = mergeTwoList(l1, l2.next)
    return l2
  }
}

//26.删除有序数组中的重复项
function removeDuplicates (nums) {
  let j = 0
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] != nums[i + 1]) {
      nums[j] = nums[i]
      j++
    }
  }
  return j
}
// console.log(removeDuplicates([0, 0, 1, 1, 1, 2, 2, 3, 3, 4]))

//27.移除元素
function removeElement (nums, val) {
  let j = 0
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] !== val) {
      nums[j] = nums[i]
      j++
    }
  }
  return j
}
console.log(removeElement([0, 1, 2, 2, 3, 0, 4, 2], 2))

//28.实现strStr()
function subStr (haystack, needle) {
  let n = haystack.length
  let m = needle.length
  for (let i = 0; i + m <= n; i++) {
    let flag = true
    for (let j = 0; j < m; j++) {
      if (haystack[i + j] !== needle[j]) {
        flag = false
        break
      }
    }
    if (flag) {
      return i
    }
  }
  return -1
}
// console.log(subStr('hello', 'lll'))

//35 搜索插入位置
function searchInsert (nums, val) {
  let left = 0, right = nums.length - 1
  while (left <= right) {
    let mid = left + ~~((right - left) / 2)
    if (nums[mid] === val) {
      return mid
    } else if (nums[mid] < val) {
      left = mid + 1
    } else {
      right = mid - 1
    }
  }
  return left
}
console.log(searchInsert([1, 3, 5, 6], 5))

//38.外观数列
var countAndSay = function (n) {
  if (n === 1) return '1'
  const temp = countAndSay(n - 1).match(/(\d)\1*/g)
  let result = ''
  for (let i = 0; i < temp.length; i++) {
    result += (temp[i].length + '' + temp[i].substring(0, 1))
  }
  return result
};

console.log(countAndSay(5))

//53. 最大子序和
function maxSubArrayDP (nums) {
  for (let i = 0; i < nums.length; i++) {
    if (nums[i - 1] > 0) {
      nums[i] = nums[i] + nums[i - 1]
    }
  }
  return Math.max(...nums)
}
function maxSubArray (nums) {
  let pre = 0, maxAns = nums[0]
  for (let i = 0; i < nums.length; i++) {
    pre = Math.max(pre + nums[i], nums[i])
    maxAns = Math.max(pre, maxAns)
  }
  return maxAns
}
console.log(maxSubArray([0]))

//58.最后一个单词的长度
function lengthOfLastWord (s) {
  let len = 0
  for (let i = s.length - 1; i >= 0; i--) {
    if (s[i] != " ") {
      len ++
    }else {
      if (len > 0) {
        break
      }
    }
  }
  return len
}
// console.log(lengthOfLastWord('hello wo'))

// 66 加一
function plusOne(digits) {
  let len = digits.length
  for (let i = len-1; i >= 0; i--) {
      digits[i] ++
      digits[i] %= 10
      if (digits[i] != 0) {
        return digits
      }
  }
  digits = [...Array(len+1)].map(_=>0)
  digits[0] = 1
  return digits
}
console.log(plusOne([9,9,9]))




```
