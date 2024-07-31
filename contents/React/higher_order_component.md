# 📚 HOC (Higher-Order-Component)


## 📖 고차 함수 (HOF)란?
- 고차 함수란 다른 함수를 인자로 받거나 함수는 반환하는 함수
- 리액트에서는 고차 컴포넌트가 고차 함수를 활용한 일반적 패턴

</br>

## 📖 고차 컴포넌트 (HOC)란?
- 컴포넌트 로직을 재사용하기 위한 리액트의 고급 기술
- HOC는 React API의 일부가 아니며 구성적 특성에서 나오는 패턴
- 컴포넌트는 props를 UI로 변환하는 반면, 고차 컴포넌트는 컴포넌트를 새로운 컴포넌트로 변환

## 🔍 예시코드
```js
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```
- 고차 컴포넌트는 Redux의 connect와 Relay의 createFragmentContainer와 같은 3rd 파티 React 라이브러리에서 흔하게 볼 수 있음

</br>

## 📖 고차 컴포넌트의 활용
### 📍 코드 재사용
- 여러 컴포넌트에서 공통적으로 사용되는 로직이 있다면 HOC로 만들어 재사용 가능
- 예를 들어 인증 체크나 권한 관리 등의 로직은 애플리케이션 전반에서 사용 
</br>

## 🔍 예시코드
```js
// withAuthentication.js
import React, { useEffect, useState } from 'react';
import { auth } from './auth';

const withAuthentication = (WrappedComponent) => {
  const AuthenticatedComponent = (props) => {
    const [isAuthenticated, setIsAuthenticated] = useState(false);

    useEffect(() => {
      auth.isAuthenticated().then((authenticated) => {
        setIsAuthenticated(authenticated);
      });
    }, []);

    return isAuthenticated ? (
      <WrappedComponent {...props} />
    ) : (
      <div>Loading...</div>
    );
  };

  return AuthenticatedComponent;
};

export default withAuthentication;

// MyComponent.js
import React from 'react';
import withAuthentication from './withAuthentication';

const MyComponent = (props) => {
  return <div>My Component</div>;
};

export default withAuthentication(MyComponent);
```

</br>

### 📍 Props 조작
- HOC는 감싸고 있는 컴포넌트에 props를 전달할 때, 추가적인 props를 합쳐서 전달 가능

## 🔍 예시코드
```js
// withLoadingIndicator.js
import React, { useState, useEffect } from 'react';

const withLoadingIndicator = (WrappedComponent) => {
  const ComponentWithLoadingIndicator = (props) => {
    const [isLoading, setIsLoading] = useState(true);

    useEffect(() => {
      // 데이터 로딩 완료 후 isLoading 상태 변경
      const timer = setTimeout(() => {
        setIsLoading(false);
      }, 2000);

      return () => clearTimeout(timer);
    }, []);

    return isLoading ? <div>Loading...</div> : <WrappedComponent {...props} />;
  };

  return ComponentWithLoadingIndicator;
};

export default withLoadingIndicator;

// MyComponent.js
import React from 'react';
import withLoadingIndicator from './withLoadingIndicator';

const MyComponent = (props) => {
  return <div>My Component</div>;
};

export default withLoadingIndicator(MyComponent);
```

</br>

### 📍 정리

- HOC를 사용하면 코드 재사용성, 유연성, 가독성 측면에서 이점
- 과도하게 코드가 복잡해지지 않도록 적절한 수준에서 사용 필요
- React hooks 등장 후 커스텀 hook 사용하는 경우 많음

</br>


## 🗂️ 참고
[Velog - 고차컴포넌트란?](https://velog.io/@osw7875/%EA%B3%A0%EC%B0%A8-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8HOC-Higher-Order-Component%EB%9E%80)