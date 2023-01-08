 /**
* 如果顶端有 10 个台阶，爬到 10 的方法有从 8 到 10，或者从 9 到 10 两种方法。爬到 9 层也是一样。
* 现在有 n 个台阶，那么爬到 n 的方法有 （n-1）=> n 和 （n-2）=> n，两种方法。
* 如果台阶是 1，那么只有 1 种方法。
* 那么到 n 个台阶，总共需要 (n-1)的方法加上(n-2)的方法。类似于菲波那切数列，1，1，2，3，5，8，13...，他的规律是前两个数相加得到第三个数。
*   @param n 传入的台阶数
*   @returns {number} 返回几种不同的方法
*/
function step(n) {
   if (Number.isInteger(n)) {
       if (n <= 1) {
           return n;
       }

       let n1 = 1;
       let n2 = 1;
       let sum = 0;
       for (let i = 2; i <= n; i++) {
           sum = n1 + n2;
           n1 = n2;
           n2 = sum;
       }

       return sum;
   } else {
       throw console.error('台阶数量错误，请输入整数');
   }
}