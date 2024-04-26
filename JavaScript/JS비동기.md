# 비동기

### 동기(Synchronous)와 비동기(Asynchronous)

### 동기: 순차적으로 코드 실행 O

### 비동기 : 순차적으로 코드 실핼 X

## 콜백(Callback) 패턴

```javascript
const a = () => {
  setTimout(() => {
    console.log(1);
  }, 1000);
};
const b = () => console.log(2);

a();
b();
// 2가 먼저 출력 되고 1초후에 1이 출력되는 비동기 코드
```

```javascript
const a = (callback) => {
  setTimout(() => {
    console.log(1);
    callback();
  }, 1000);
};
const b = () => console.log(2);

a(() => {
  b();
});
// 이렇게 하면 1과2가 1초후에 1,2순서대로 출력된다
```

```javascript
const a = (callback) => {
  setTimout(() => {
    console.log(1);
    callback();
  }, 1000);
};
const b = (callback) => {
  setTimout(() => {
    console.log(2);
    callback();
  }, 1000);
};
const c = (callback) => {
  setTimout(() => {
    console.log(3);
    callback();
  }, 1000);
};
const d = () => console.log(4);
a(() => {
  b(() => {
    c(() => {
      d();
    });
  });
});
// 이렇게 하면 1초후에 1 또1초뒤에 2 또1초뒤에 3,4순서대로 출력된다
// 콜백지옥
```

## Promise

```javascript
const a = (callback) => {
  setTimout(() => {
    console.log(1);
    callback();
  }, 1000);
};
const b = () => console.log(2);

a(() => {
  b();
});
```

이 코드를

```javascript
const a = () => {
  return new Promise((resolve) => {
    setTimout(() => {
      console.log(1);
      resolve();
    }, 1000);
  });
};
const b = () => console.log(2);

a().then(() => {
  b();
});
```

이렇게 사용가능<br/>
<br/>
결과적으로

```javascript
const a = () => {
  return new Promise((resolve) => {
    setTimout(() => {
      console.log(1);
      callback();
    }, 1000);
  });
};
const b = () => {
  return new Promise((resolve) => {
    setTimout(() => {
      console.log(2);
      resolve();
    }, 1000);
  });
};
const c = () => {
  return new Promise((resolve) => {
    setTimout(() => {
      console.log(3);
      resolve();
    }, 1000);
  });
};
const d = () => console.log(4);

a()
  .then(() => {
    return b();
  })
  .then(() => {
    return c();
  })
  .then(() => {
    d();
  });

a()
  .then(() => b())
  .then(() => c())
  .then(() => b());

a()
  .then(b)
  .then(c)
  .then(d)
  .then(() => console.log('done'));
```

`.then`을 계속 붙여서 사용가능

##### promise 예제

```javascript
const getMovies = (movieName) => {
  return new Promise((resolve) => {
    fetch('https://www.omdbapi.com/?apikey=7035c60c&s=${movieName}')
      .then((res) => res.json())
      .then((res) => {
        console.log(res);
        resolve();
      });
  });
};

getMovies('frozen')
  .then(() => {
    console.log('겨울왕국');
    return getMovies('avengers');
  })
  .then(() => {
    console.log('어벤져스');
    return getMovies('avatar');
  })
  .then(() => {
    console.log('아바타');
  });
```

## Async Await패턴

```javascript
const a = () => {
  return new Promise((resolve) => {
    setTimout(() => {
      console.log(1);
      resolve();
    }, 1000);
  });
};
const b = () => console.log(2);

a().then(() => {
  b();
});
```

`a().then(() => { b() })` 이 부분을

```javascript
await a();
b();
```

이렇게 사용할수 있지만 `await`는 함수에 씌어져 있어야 사용가능

```javascript
const wrap = async () => {
  await a();
  b();
};
```

이렇게 사용할수있다

```javascript
const getMovies = (movieName) => {
  return new Promise((resolve) => {
    fetch('https://www.omdbapi.com/?apikey=7035c60c&s=${movieName}')
      .then((res) => res.json())
      .then((res) => {
        console.log(res);
        resolve();
      });
  });
};

getMovies('frozen')
  .then(() => {
    console.log('겨울왕국');
    return getMovies('avengers');
  })
  .then(() => {
    console.log('어벤져스');
    return getMovies('avatar');
  })
  .then(() => {
    console.log('아바타');
  });
```

고쳐보자

```javascript
const wrap = asvnc () => {
  await getMovies('frozen')
  console.log('겨울왕국')
  await getMovies('avengers')
  console.log('어벤져스')
  await getMovies('avatar')
  console.log('아바타')
}
wrap()
```

완성!
