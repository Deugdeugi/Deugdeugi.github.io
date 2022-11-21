1. async await 개념에 대해서 다시 정리

2. async 함수는 원래 promise를 반환한다 
=> 명시적으로 return하지 않으면? undefined로 반환됨.
https://stackoverflow.com/questions/70785392/async-await-not-returning-value-as-expected

3. 요 두 개는 반환의 위치가 다르다.
async function test(){
    await foo(1, 2000)
    await foo(2, 500)
    await foo(3, 1000)
}

function foo(num, sec){
    return new Promise(function(resolve, reject){
        setTimeout( function(){
            console.log(num);
            resolve("async는 Promise방식을 사용합니다.");
        }, sec);
    });
}
test();

==========================================================

async function test(){
    await foo(1, 2000)
    await foo(2, 500)
    await foo(3, 1000)
}

function foo(num, sec){
        setTimeout(async() => {
            console.log(num);
            return "async는 Promise방식을 사용합니다.";
        }, sec);
}
test();