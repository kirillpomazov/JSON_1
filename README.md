HW_2 Postman

1. Отправить запрос

`http://162.55.220.72:5005/first`


2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

3. Проверить, что в body приходит правильный string
```js
pm.test("Test string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!");
});
```

<hr>

1. Отправить запрос


`http://162.55.220.72:5005/user_info_3`


2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

3. Спарсить response body в json
```js
let jsonData = pm.response.json();
```
4.  Переводим string в int
```js
let age = +jsonData.age
```
5. Проверить, что name в ответе равно name s request (name вбить руками.)
```js
pm.test("Test name", function () {
    pm.expect(jsonData.name).to.eql("Kirill");
});
```
6. Проверить, что age в ответе равно age s request (age вбить руками.)
```js
pm.test("Test age", function () {
    pm.expect(age).to.eql(35);
});
```

7. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```js
pm.test("Test salary", function () {
    pm.expect(jsonData.salary).to.eql(2500);
});
```

8. Спарсить request.
```js
let parsReguest = request.data;
// создадим переменную и  преобразуем ее в int 
let reqSalary = +parsReguest.salary;
```

9. Проверить, что name в ответе равно name s request (name забрать из request.)
```js
pm.test("Response name = Request name", function () {
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```

10. Проверить, что age в ответе равно age s request (age забрать из request.)
```js
pm.test("Response age = Request age", function () {
    pm.expect(jsonData.age).to.eql(reqData.age);
});
```

11. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```js
pm.test("Test salary request", function () {
    pm.expect(jsonData.salary).to.eql(reqSalary);
});
```

12. Вывести в консоль параметр family из response.
```js
console.log ("Family", jsonData.family)
```

13. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```js
pm.test("Test salary response vs request", function () {
    pm.expect(jsonData.family.u_salary_1_5_year).to.eql(reqSalary*4);
});
```

<hr>

1. Отправить запрос.

`http://162.55.220.72:5005/object_info_3`


2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

3. Спарсить response body в json.
```js
let jsonData = pm.response.json();
```

4. Спарсить request.
```js
llet parsReguest = pm.request.url.query.toObject()
// создадим переменную requestSalary и присвоим ей преобразованное в int
let requestSalary = +parsReguest.salary
```

5. Проверить, что name в ответе равно name s request (name забрать из request.)
```js
pm.test("Test name response vs name request", function () {
    pm.expect(jsonData.name).to.eql(parsReguest.name);
});
```

6. Проверить, что age в ответе равно age s request (age забрать из request.)
```js
pm.test("Test age response vs age request", function () {
    pm.expect(jsonData.age).to.eql(parsReguest.age);
});
```

7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```js
pm.test("Test salary response vs salary request", function () {
    pm.expect(jsonData.salary).to.eql(requestSalary);
});
```

8. Вывести в консоль параметр family из response.
```js
console.log("Family", jsonData.family)
```

9. Проверить, что у параметра dog есть параметры name.
```js
pm.test("Dog have name", function () {
    pm.expect(jsonData.family.pets.dog).to.include.keys("name");
});
```

10. Проверить, что у параметра dog есть параметры age.
```js
pm.test("Dog have age", function () {
    pm.expect(jsonData.family.pets.dog).to.include.keys("age");
});
```

11. Проверить, что параметр name имеет значение Luky.
```js
pm.test("Name is Luky", function () {
    pm.expect(jsonData.family.pets.dog.name).to.eql("Luky");
});
```

12. Проверить, что параметр age имеет значение 4.
```js
pm.test("Age is 4", function () {
    pm.expect(jsonData.family.pets.dog.age).to.eql(4);
});
```

<hr>
1. Отправить запрос.

`http://162.55.220.72:5005/object_info_4`


2. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});;
```

3. Спарсить response body в json.
```js
let parse_response = pm.response.json();
```

4. Спарсить request.
```js
let parse_request = pm.request.url.query.toObject()
// создадим переменную parse_request_salary и присвоим ей преобразованное в int
let parse_request_salary = +parse_request.salary
```

5. Проверить, что name в ответе равно name s request (name забрать из request.)
```js
pm.test("Name request == name response", function () {
    pm.expect(response_name).to.eql(parse_request.name);
});
```

6. Проверить, что age в ответе равно age из request (age забрать из request.)
```js

// создадим переменную parse_request_age и присвоим ей преобразованное в int
let parse_request_age = +parse_request.age

pm.test("Name request == name response", function () {
    pm.expect(parse_response.age).to.eql(parse_request_age);
});
```

7. Вывести в консоль параметр salary из request.
```js
console.log("Requset Salary =", parse_request.salary);
```

8. Вывести в консоль параметр salary из response.
```js
console.log("Response Salary = ", parse_response.salary);
```

9. Вывести в консоль 0-й элемент параметра salary из response.
```js
console.log("Response Salary 0 =", parse_response.salary[0]);
```

10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```js
console.log("Response Salary 1 =", parse_response.salary[1]);
```

11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```js
console.log("Response Salary 2 =", parse_response.salary[2]);
```

12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```js
pm.test("Response salary 0 == Request salary", function () {
    pm.expect(parse_response.salary[0]).to.eql(parse_request_salary);
});
```

13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```js
resp_salary_1 = +parse_response.salary[1];
pm.test("Response salary 1 == Request salary", function () {
    pm.expect(resp_salary_1).to.eql(parse_request_salary*2);
});
```

14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```js
let resp_salary_2 = +parse_response.salary[2];
pm.test("Response salary 2 == Request salary", function () {
    pm.expect(resp_salary_2).to.eql(parse_request_salary*3);
});
```

15. Создать в окружении переменную name

16. Создать в окружении переменную age

17. Создать в окружении переменную salary

18. Передать в окружение переменную name
```js
pm.environment.set("name", parse_request.name);
```

19. Передать в окружение переменную age
```js
pm.environment.set("age", parse_request_age);
```

20. Передать в окружение переменную salary
```js
pm.environment.set("salary", parse_request.salary);
```

21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```js
let response_salary = parse_response.salary
for (let i = 0; i <= 2; i++) {
	console.log("Cycle salary" , response_salary[i]);
}
// или
// for (let i = 0; i < response_salary.length; i += 1) {
// console.log("TEST" , response_salary[i]);
//}

```

<hr>



1. Вставить параметр salary из окружения в request

2. Вставить параметр age из окружения в age

4. Вставить параметр name из окружения в name

5. Отправить запрос

`http://162.55.220.72:5005/user_info_2`

6. Статус код 200
```js
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

7. Спарсить response body в json.
```js
let respData = pm.response.json();
```

8. Спарсить request.
```js
let reqData = request.data;
```

9. Проверить, что json response имеет параметр start_qa_salary
```js
pm.test("JSON response have start_qa_salary ", function () {
    pm.expect(respData).to.have.property("start_qa_salary");
});
```

10. Проверить, что json response имеет параметр qa_salary_after_6_months
```js
pm.test("JSON response have qa_salary_after_6_months ", function () {
    pm.expect(respData).to.have.property("qa_salary_after_6_months");
});
```

11. Проверить, что json response имеет параметр qa_salary_after_12_months
```js
pm.test("JSON response have qa_salary_after_12_months ", function () {
    pm.expect(respData).to.have.property("qa_salary_after_12_months");
});
```

12. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```js
pm.test("JSON response have qa_salary_after_1.5_year", function () {
    pm.expect(respData).to.have.property("qa_salary_after_1.5_year");
});
```

13. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```js
pm.test("JSON response have qa_salary_after_3.5_years", function () {
    pm.expect(respData).to.have.property("qa_salary_after_3.5_years");
});
```

14. Проверить, что json response имеет параметр person
```js
pm.test("JSON response have person", function () {
    pm.expect(respData).to.have.property("person");
});
```

15. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```js
pm.test("respData.start_qa_salary === salary from request", function () {
    pm.expect(respData.start_qa_salary).to.eql(+reqData.salary);
});
```

16. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```js
pm.test("a_salary_after_6_months === salary*2 from request", function () {
    pm.expect(respData.qa_salary_after_6_months).to.eql(reqData.salary*2);
});
```

17. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```js
pm.test("qa_salary_after_12_months === salary*2.7 from request", function () {
    pm.expect(respData.qa_salary_after_12_months).to.eql(reqData.salary*2.7);
});
```

18. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```js
pm.test("qa_salary_after_1.5_year === salary*3.3 from request", function () {
    pm.expect(respData['qa_salary_after_1.5_year']).to.eql(reqData.salary*3.3);
});
```

19. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```js
pm.test("qa_salary_after_3.5_year === salary*3.8 from request", function () {
    pm.expect(respData['qa_salary_after_3.5_years']).to.eql(+reqData.salary*3.8);
});
```

20. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```js
pm.test("First element person u_name === request salary", function () {
    pm.expect(respData.person.u_name[1]).to.eql(+reqData.salary);
});
```

21. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```js
pm.test("u_gae === request age", function () {
    pm.expect(respData.u_age).to.eql(+reqData.age);
});
```

22. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```js
pm.test("u_salary_5_years === salary*4.2 from request", function () {
    pm.expect(respData.person["u_salary_5_years"]).to.eql(+reqData.salary*4.2);
});
```

23. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```js
for(let KEY in respData.person) {
   if(typeof(respData.person[KEY]) == "object"){
       for(let i = 0; i < Object.keys(respData.person[KEY]).length; i++){
           console.log(respData.person[KEY][i]);
       }
   }
   else if(typeof(respData.person[KEY]) != "object") {
        console.log(respData.person[KEY]);
   }
}
```

