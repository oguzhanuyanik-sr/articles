# Codewars TypeScript Çözümleri

#### 36) Sayılardan oluşan bir string verilir, rakam 5'den küçükse 0, 5'den büyükse 1 ile değiştirilmelidir.

Input:  '158' <br>
Output: '011'

```
export const fakeBin = (x:string):string => {
  return [...x].map((n) => parseInt(n) < 5 ? '0' : '1').join('');
};
```
```
export const fakeBin = (x:string):string => x.replace(/\d/g, n => Number(n) < 5 ? '0' : '1');
```

#### 35) Boolean olarak verilen değer farklı yöntemlerle string türüne dönüştürülmelidir.

Input:  true <br>
Output: 'true'

```
export const booleanToString = (b:boolean):string => {
  return b.toString();
};
```
```
export const booleanToString = (b:boolean):string => {
  return String(b)
};
```
```
export const booleanToString = (b:boolean):string => `${b}`;
```
```
export const booleanToString = (b:boolean | string):string =>  b + '';
```

#### 34) String bir şekilde verilen sayı farklı yöntemlerle number türüne dönüştürülmelidir.

Input:  '1' <br>
Output: 1

```
export const stringToNumber = (str: string): number => +str;
```
```
export function stringToNumber(str: string): number {
  return Number(str);
}
```
```
export function stringToNumber(str: string): number {
  return parseInt(str);
}
```
#### 33) Sayılardan oluşan bir array verilir, en küçük sayı döndürülmelidir.

Input:  [1, 2, -1] <br>
Output: -1

```
export function findSmallestInt(args: number[]): number {
  return Math.min(...args);
}
```
```
export const findSmallestInt = (args: number[]): number => args.sort((a, b) => a - b)[0];
```

#### 32) Sayılardan oluşan bir array verilir, tüm sayıların karesi alınıp toplanmalıdır. Array boş ise 0 dönmelidir.

Input:  [1, 2] <br>
Output: 5

```
export function squareSum(numbers: number[]): number {
    return numbers.reduce((prev, curr) => prev + curr * curr, 0);
}
```

#### 31) Negatif ve pozitif sayılardan oluşan bir array verilir. Pozitif olanlar toplanıp döndürülmelidir. Array boş ise 0 dönmelidir.

Input:  [1,-3, 5] <br>
Output: 6

```
export function positiveSum(arr:number[]):number {
  let positiveArr:number[] = arr.filter(item => item > 0);
  
  return positiveArr.length ? positiveArr.reduce((sum, num) => {
    return sum + num;
  }) : 0;
}
```
```
export function positiveSum(arr:number[]):number {
  return arr.filter((e) => e >= 0).reduce((acc, e) => acc + e , 0)
}
```
```
export function positiveSum(arr:number[]):number {
  return arr.reduce((sum, n) => n > 0 ? sum + n : sum, 0);
}
```

#### 30) İki string verilir ve uzunluklarına göre kısa + uzun + kısa şeklinde birleştirilerek yeni bir string döndürülmelidir.

Input:  'a', 'bb' <br>
Output: 'abba'

```
export function shortLongShort(a:string, b:string): string {
  return a.length > b.length ? `${b}${a}${b}` : `${a}${b}${a}`;
}
```
```
export function shortLongShort(a:string, b:string): string {
  let [short, long] = [a,b].sort((a, b) => a.length - b.length);
  return `${short}${long}${short}`;
}
```

#### 29) Sayılardan oluşan bir array ve x sayısı verilir. Array içerisindeki sayılardan, x sayısına tam bölünenler bir array olarak döndürülmelidir.

Input:  [1, 2, 3, 4], 2 <br>
Output: [2, 4]

```
export function divisibleBy(numbers: number[], x: number): number[]{
  return numbers.filter((n: number) => n % x === 0);
}
```


#### 28) Bir sayı verilir, verilen sayı ters çevrilerek ve number array olarak döndürülmelidir.

Input:  1, 2, 3, 4 <br>
Output: [4, 3, 2, 1]

```
export const digitize = (n: number): number[] => {
  return n.toString().split('').reverse().map(function (item) {
    return parseInt(item);
  });
};
```
```
export const digitize = (n: number): number[] => {
  return [...n.toString()].map(Number).reverse();
};
```


#### 27) Verilen yılın hangi yüzyıla ait olduğu döndürülmelidir (1881 = 19).

Input:  2000 <br>
Output: 20

```
export const centuryFromYear = (year: number): number => {
  return Math.ceil(year / 100);
};
```
```
export const centuryFromYear = (year: number): number => {
  return year % 100 === 0 ? year / 100 : Math.trunc(year / 100) + 1
};
```


#### 26) a, b ve c sayıları verilir. +, * ve () matematiksel operatörleri kullanarak ulaşılabilecek en büyük sonuç döndürülmelidir.

Input:  1, 2, 3 <br>
Output: 9

```
export function expressionsMatter(a: number, b: number, c: number): number {
   return Math.max(a*b*c, (a+b)*c, a*(b+c), a+b+c);
}
```


#### 25) a ve b sayıları parametre olarak verilir ve a'dan b'ye kadar olan sayılardan oluşan bir array döndürülmelidir (a ve b dahil, a < b).

Input:  1, 4 <br>
Output: [1, 2, 3, 4]

```
export function between(a: number, b: number): number[] {
  const arr = [];
  
  for(let i = a; i <= b; i++) {
    arr.push(i);
  }
  
  return arr;
}
```
```
export function between(a: number, b: number): number[] {
  return Array.from({length: b - a + 1}, (_, j) => j + a);
}
```
```
export function between(a: number, b: number): number[] {
  return [...Array(b-a+1).keys()].map(_ => _+a);
}
```

#### 24) Bir sayı parametre olarak verilir ve o sayıdan 1'e kadar olan tek sayıların adeti döndürülmelidir.

Input:  7 <br>
Output: 3

```
export const oddCount = (n: number): number => Math.floor(n/2);
```


#### 23) Bir n sayı verilir ve 0'dan n-1'e kadar olan sayılardan oluşan bir array döndürülmelidir. Ayrıca n'in boş gelme ihtimaline karşı varsayılan bir değere sahip olmalıdır.

Input:  5 <br>
Output: [0, 1, 2, 3, 4]

```
export const arr = (n: number = 0): number[] => Array.from({length: n}, (_, i) => i);
```
```
export const arr = (n: number = 0): number[] => [...Array(n).keys()];
```


#### 22) Babanın yaşı ve oğlunun yaşı parametre olarak verilir. Babanın yaşı; kaç yıl önce veya kaç yıl sonra oğlunun iki katıdır veya iki katı olacaktır.

Input:  55, 30 <br>
Output: 5

```
export function twiceAsOld(dad: number, son: number): number {
  return Math.abs(dad - son * 2)
}
```


#### 21) Sayılardan oluşan bir array parametre olarak verilir. Bu sayıların, tam sayı bir karekökü varsa karekökünü  eğer yoksa karesini alarak yeni bir dizi döndürülmelidir.

Input:  [2, 3, 4] <br>
Output: [4, 9, 2]

```
export function squareOrSquareRoot(array:number[]) : number[] {
  return array.map(function (num) {
    let sqrt: number = Math.sqrt(num);
    
    return sqrt === Math.floor(sqrt) ? sqrt : num * num;
  });
}
```
```
export function squareOrSquareRoot(array:number[]) : number[] {
  return array.map(a => Math.sqrt(a) % 1 == 0 ? Math.sqrt(a) : (a * a));  
}
```
```
export const squareOrSquareRoot = (array:number[]) => array.map(v => Number.isInteger(Math.sqrt(v)) ? Math.sqrt(v) : v ** 2 )
```


#### 20) Sayılardan oluşan bir array verilir ve tüm sayılar çarpılarak sonuç döndürülmelidir.

Input:  [1, 2, 3] <br>
Output: 6

```
export const grow = (arr: number[]): number => arr.reduce((result, i) => result * i);
```
#### 19) Bir araç 40$'a kiralanmaktadır. 3 gün veya daha fazla kiralanırsa 20$ indirim, 7 gün veya daha fazla kiralanırsa 50$ indirim yapılmaktadır. İndirimlerin sadece bir tanesi geçerli olacaktır. Gün sayısı parametre olarak verilir, tutar döndürülmelidir. 

Input:  3 <br>
Output: 100

```
export function rentalCarCost(d: number): number {
  if (d >= 7) return d * 40 - 50;
  if (d >= 3) return d * 40 - 20
  return d * 40;
}
```
```
export const rentalCarCost = (d: number): number => {
  return d < 3 ? 40 * d : d >= 3 && d < 7 ? 40 * d - 20 : 40 * d - 50;
}
```
```
export function rentalCarCost(d: number): number {
  let total = d*40
  if(d >= 3 && d < 7) total -= 20
  if(d >= 7) total -= 50
  
  return total
}
```
#### 18) String veya number bir array ile birlikte bir number veya bir string verilir. Array'in içerisinde bulunuyorsa true, bulunmuyorsa false döndürmelidir.

Input: [1, 2, 3], 3 <br>
Output: true

```
export const check = (a: (number | string)[], x: number | string): boolean => a.indexOf(x) !== -1;
```
```
export const check = (a: any[], x: any): boolean => {
  return a.includes(x)
}
```
```
export const check = (a: (number | string)[], x: number | string): boolean => {
    return a.some(n => n === x);
}
```
#### 17) Parametre olarak verilen sayı çift ise 8 ile tek ise 9 ile çarpılarak sonuç döndürülmelidir.

Input: 2 <br>
Output: 16

```
export const simpleMultiplication = (num: number): number => num * (num % 2 === 0 ? 8 : 9);
```
```
export function simpleMultiplication(num: number): number{
  return num * [8, 9][num % 2];
}
```
#### 16) Sayılardan oluşan iki array verilir ve toplamları number olarak döndürülmelidir.

Input: [1, 2, 3], [4] <br>
Output: 10

```
export const arrayPlusArray = (arr1: number[], arr2: number[]): number => [...arr1, ...arr2].reduce((sum, i) => sum + i);
```
```
export const arrayPlusArray = (a : any, b : any) : any => eval(a.concat(b).join`+`);
```
```
export const arrayPlusArray = (arr1 : number[], arr2 : number[]) => arr1.concat(arr2).reduce((a, b) => a + b);
```
#### 15) Üç sınav notu verilir ve ortalamasına göre harf notu döndürülmelidir.

Input: 100, 90, 90 <br>
Output: 'A'

```
export function getGrade(a: number, b: number, c: number) {
  let avg = (a + b + c) / 3;
  
  return avg < 60 ? "F" : avg < 70 ? "D" : avg < 80 ? "C" : avg < 90 ? "B" : "A";
}
```
```
export function getGrade(a: number, b: number, c: number) {
  const score = (a + b + c) / 3
  let grade = 'F'
  
  switch (true) {
      case score >= 90 :
        grade = 'A'
        break
      case score >= 80 :
        grade = 'B'
        break
      case score >= 70 :
        grade = 'C'
        break
      case score >= 60 :
        grade = 'D'
        break
  }
  
  return grade
}
```
#### 14) Parametre olarak verilen stringin, ilk ve son harfi silinerek döndürülmelidir.

Input: 'person' <br>
Output: 'erso'

```
export const removeChar = (str: string):string => str.slice(1, -1);
```
```
export const removeChar = (str:string) => str.substring(1, str.length-1);
```
```
export function removeChar(str: string): string {
  const arr = [...str];
  
  arr.pop();
  arr.shift();
  
  return arr.join('');
}
```
#### 13) Verilen sayı ve 'sheep...' stringi birleştirilmeli, verilen sayı kadar tekrarlanarak döndürülmelidir.

Input: 3 <br>
Output: '1 sheep...2 sheep...3 sheep...'

```
export function countSheep(num: number): string {
  var result: string = '';
  
  for (let i = 1; i <= num; i++) {
    result += `${i} sheep...`;
  }
  
  return result;
}
```
```
export function countSheep(num: number): string {
  return Array.from({length: num}, (_, i) => `${i + 1} sheep...`).join('');
}
```
#### 12) n, x ve y sayıları verilir ve n sayısının hem x hem de y'ye bölünebilirliğine göre true veya false döndürülmelidir.

Input: 12, 3, 4 <br>
Output: true

```
export const isDivisible = (n: number, x:number, y:number): boolean => n % x === 0 && n % y === 0;
```
```
export const isDivisible = (n: number, x:number, y:number): boolean => !(n % x) && !(n % y);
```
#### 11) Sayılardan oluşan bir array ve bir sayı parametre olarak verilir. Array'in içerisinde verilen sayıya karşılık gelen index'in o sayı kadar kuvveti alınır. Eğer array'de karşılık gelen bir eleman yoksa -1 döndürülür.

Input: [0, 1, 2], 2 <br>
Output: 4

```
export function index(array: number[], n: number): number {
  return array[n] ** n || -1;
}
```
```
export function index(array: number[], n: number): number {
  return n < array.length ? Math.pow(array[n], n) : -1;
}
```
```
export function index(array: number[], n: number): number {
  const res: number = array[n] ** n;
  return isNaN(res) ? -1 : res;
}
```
#### 10) Bir string verilir ve bu string 'alligator' ise 'small', değilse 'wide' döndürülmelidir.

Input: 'aLLigatoR' <br>
Output: 'small'

```
export const mouthSize = (animal: string):string => animal.toLowerCase() === 'alligator' ? 'small' : 'wide';
```
```
export const mouthSize = (animal: string): string => /alligator/i.test(animal) ? 'small' : 'wide';
```
#### 9) Sayılardan oluşan bir array verilir ve tekrarlayan değerler silinerek aynı sıra ile array olarak döndürülmelidir.

Input: [1, 1, 2, 3, 3] <br>
Output: [1, 2, 3]

```
export const distinct = (a: number[]): number[] => {
  let arr = [];
  
  for (let num of a) {
    arr.indexOf(num) === -1 && arr.push(num);
  }
  
  return arr;
}
```
```
export const distinct = (a: number[]): number[] => [...new Set(a)];
```
```
export const distinct = (a: number[]): number[] => {
    const resultArray: number[] = [];
    
    a.forEach(number => {
        if (resultArray.indexOf(number) === -1) {
            resultArray.push(number);
        }
    });

    return resultArray;
}
```
#### 8) String bir parametre verilir, tersi döndürülmelidir.

Input: 'Doe' <br>
Output: 'eoD'

```
export const solution = (str: string): string => str.split('').reverse().join('');
```
```
export const solution = (str: string): string => [...str].reverse().join('');
```
#### 7) İsim ve soyisim formatında iki kelimelik bir string verilir. Baş harfleri büyük olacak ve isimden sonra nokta gelecek şekilde string döndürülmelidir.

Input: 'John doe' <br>
Output: 'J.D'

```
export function abbrevName(name: string): string {
  var arr: string[] = name.split(' ');

  return arr[0][0].toUpperCase() + '.' + arr[1][0].toUpperCase();
}
```
```
export const abbrevName = (name: string): string => name.split(" ").map((item) => item[0].toUpperCase()).join('.');
```
```
export function abbrevName(name: string): string {
    return name.toUpperCase().replace(/(\w)\w* (\w)\w*/, '$1.$2')
}
```
#### 6) String bir parametre verilir. Tüm harfleri büyükse true, değilse false dönmelidir.

Input: 'TEST' <br>
Output: true

```
export const isUpperCase = (str: string): boolean => str === str.toUpperCase();
```
```
export function isUpperCase(str: string): boolean {
    return str.match(/[a-z]/) === null;
}
```
```
export function isUpperCase(str: string): boolean {
    for (let i = 0; i < str.length; i++) {
        if (str.charCodeAt(i) >= 97 && str.charCodeAt(i) <= 122) return false;
    }
    return true;
}
```
```
export function isUpperCase(str: string): boolean {
    return /^[A-Z\s]+$/.test(str);
}
```
#### 5) Sayılardan oluşan bir array verilir, ortalaması döndürülmelidir. Eğer verilen array boş ise 0 dönmelidir.

Input: [1, 2, 3] <br>
Output: 2

```
export const findAverage = (array: number[]): number => array.length > 0 ? array.reduce((sum, i) => sum + i) / array.length : 0;
```
```
export function findAverage(array: number[]): number {
    if (array.length === 0) return 0

    let total: number = 0

    array.forEach(num => total += num)
    
    return total / array.length;
}
```
#### 4) Pozitif ve negatif sayılardan oluşan bir array verilir. Pozitif sayıların adeti ve negatif sayıların toplamından oluşan 2 elemanlı bir array döndürülmelidir.

Input: [0, 2, 3, 0, 5, 6, 7, 8, 9, 10, -11, -12, -13, -14] <br>
Output: [8, -50]

```
export function countPositivesSumNegatives(input: Array<number> | null): number[] {
  return input && input.length ? [
    input.filter((n) => n > 0).length,
    input.filter((n) => n < 0).reduce((n1, n2) => n1 + n2, 0)
  ]: []
};
```
#### 3) 0'dan büyük bir sayı parametre olarak verilecektir. 1'den itibaren verilen sayıya kadar olan sayıların toplamı döndürülmelidir.

Input: 3 <br>
Output: 6

```
export const summation = (n:number): number=> { 
  return n*(n+1)/2;
}
```
```
export const summation = (num:number):number => { 
  var total: number = 0;
  
  for(let i= 1; i <= num; i++) {
    total += i;
  }
  
  return total;
}
```
#### 2) İki string parametre verilecektir. İlk harfleri ve son harfleri aynı ise true, değilse false döndürülmelidir.

Input: ‘Chickadee’, ‘Chocolate Cake’ <br>
Output: true

```
export function feast(beast:string, dish:string):boolean {
  return beast[0] === dish[0] && beast.slice(-1) === dish.slice(-1);
}
```
```
export const feast = (beast:string, dish:string):boolean => beast[0] === dish[0] && beast.slice(-1) === dish.slice(-1);
```

```
export function feast(beast: string, dish: string): boolean {
  return beast[0] === dish[0] && beast[beast.length - 1] === dish[dish.length - 1];
}
```
#### 1) Verilen string parametre boşlukları silinerek döndürülmelidir.

Input: 'T e s t !' <br>
Output: 'Test!'

```
export const noSpace = (x: string):string => x.split(' ').join('');
```
```
export function noSpace(x: string): string {
    return x.replace(new RegExp(' ', 'g'), '');
}
```

```
export function noSpace(x:string):string {
  return x.replace(/\s/g, '');
}
```
