# unlim-group-test-task-front

###  1.  
Какой из двух фрагментов кода не сработает и почему?
  
Фрагмент 1:
```	
	console.log( doubleNum(10) );

	let doubleNum = (num) => {
		let result = num * 2;
		return result;
	}
```  

Фрагмент 2:
```
	console.log( doubleNum(10) );

	function doubleNum(num) {
    		let result = num * 2;
		return result;
	}
```  

#### Решение:

Сработает фрагмент кода под номер два. Тут дело в том, что нужно хотя бы примерно понимать, как именно js интерпретирует функции. Функция, которая объявлена через синтаксис

```
function funcDecl() {

}
```
Она же Function Decloration будет "инициализирована" в первую очередь, до выполнения основного кода. Именно по этой причине она может быть вызвана до своего объявления

В случае же 
```
const funcExp = function() {

};

||

const funcExp = () => {

};
```
Инициализация произойдёт только тогда, когда выполнение основого потока кода дойдёт до этой строчки. Следовательно, можно расценивать такой синтаксис, как простую инициализацию переменной/константы. Очевидно, что до инициализации переменной/константы, её значение будет undefined.

https://learn.javascript.ru/function-expressions

### 2.  
Исправьте ошибку в фрагменте коде так, чтобы после компиляции в шаблоне не было лишних тегов:
```
	<template>
		<component-name
			v-for="i of count" 
			:key="i"
			v-if="i < 10" 
		/>
	</template>

	<script>
	export default {
		data() {
			return {
				count: 20;
			};
		},
	};
	</script>  
```  

#### Решение:
```
<template>
  <template
    v-for="i of count"
    :key="i"
  >
    <component-name
      v-if="i < 10"
    />
  </template>
</template>

<script>
export default {
  data() {
    return {
      count: 20
    }
  }
}
</script>
```



### 3.  
Есть массив некоторых строительных материалов, каждый элемент массива - объекты с ключами id и количества материала. Напишите функцию, которая будет возвращать oбьект в формате { "id":"count" }

```
   resources = [
			{
			   id: 1,
			   count: 13,
   			},
			{
			   id: 2,
			   count: 5,
   			}, 
			{
			   id: 3,
			   count: 24,
   			},
		      {
			   id: 4,
			   count: 101,
   			}, 
			{
			   id: 5,
			   count: 72,
   			}, 
			{
			   id: 6,
			   count: 64,
   			}, 
			{
			   id: 7,
			   count: 305,
   			}, 
			{
			   id: 8,
			   count: 67,
   			}, 
			{
			   id: 9,
			   count: 95,
   			}, 
			{
			   id: 10,
			   count: 21,
   			}, 
			{s
			   id: 11,
			   count: 37,
   			},
		   ];
```  

Ожидаемый результат: 

```
  {
				   1: 13,
				   2: 5,
				   3: 24,
				   4: 101,
				   5: 72,
				   6: 64,
				   7: 305,
				   8: 67,
				   9: 95,
				   10: 21,
				   11: 37,
			     }
```  

#### Решение:
```
function solution(data) {
  return data.reduce((t, c) => {
    t[c.id] = c.count
    return t
  }, {})
}
```
