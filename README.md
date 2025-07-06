개발의 첫 시작으로 HTML과 CSS 교육 진행 및 과제가 제출되었다. HTML 태그를 직접 쓰고 css 파일을 만들어 적용해 본 것이 워낙 오랜만이라 생소했다. 모르는 내용은 없었으나 css를 다루는 좋은 연습이 되었다.

한 주를 마무리하며 과제가 나왔다. 내용은 아래와 같은 페이지를 HTML, CSS를 사용해 구현하기.
![](https://velog.velcdn.com/images/finero-d/post/2c5c2cd2-4507-4b3e-a507-cdb1e49e5a0d/image.png)

구현하며 막혔던 순간이 세 번 있어 기록한다.

1. background-color는 상속되지 않는다.
   ![](https://velog.velcdn.com/images/finero-d/post/2e0bb53a-3909-46ce-93c9-cff9785076f7/image.png)

채팅 영역의 배경을 white로 적용하기 위해 가장 상위 div 태그에 white를 적용시켰으나 하얘진 영역은 일부였다. 확인 결과 특정 css는 상속이 되지 않는다고 하였고, 여러 해결법이 있었다. 태그에 일일이 white를 넣는 것은 세련된 것 같지 않아 아래의 코드로 해결하였다.

```
*{
	background-color: white
}
```

2. 적용되지 않는 border-radius
   마찬가지로 카드형식의 영역 귀퉁이를 부드럽게 다듬기 위해 border-radius를 주었으나 적용되지 않았다.
   ![](https://velog.velcdn.com/images/finero-d/post/da488612-93f2-4154-a65a-00966e95d9e0/image.png)
   실험을 해보니 겹친 영역들 모두 border-radius를 주면 해결된다는 것은 확인했다. 다만 더 좋은 해결 방법이 있을 것으로 생각했고, `overflow: hidden;`을 부모에게 주면, 부모 영역을 삐져나간 부분을 가려준다는 것을 확인하여 적용해 마무리했다.

3. html
   css 적용이 비일관적으로 되는 현상이 갑자기 나타나기 시작하였고, 커서로도 문제의 원인을 확인하지 못하고 있었다. 그렇게 원인을 찾던 중 css 적용의 비일관성 속에서 패턴이 보였고, 이를 실마리 삼아 찾아낸 문제는 아래와 같았다.

```html
<div class="upper">
  <img src="img.jpg" alt="img" />
      <div>
      <p>심층 분석 대화</p>
      <p>호스트 2명</p>
      </div>
  </div>
</div>

```

위 코드에서 문제를 발견하는 데 꽤 오래 걸렸다. lint가 이 정도는 자동으로 걸러줄 것이라 믿었으나 가짜 `</div>`를 걸러주지 못했다. 하필 이미지 태그와 같은 인덴트를 갖고 절묘하게 숨어있었다. 오늘 이후로 html 파일을 만들 일이 언제 또 있을지는 모르겠지만 같은 실수는 피할 수 있을 것이다.

위의 내용들을 반영하여 완성한 페이지는 아래와 같이 완성됐다. 이미지를 찾아 넣는 것은 생략하여 아무 이미지, 이모지로 대체하였다.
![](https://velog.velcdn.com/images/finero-d/post/ec970f1b-ef16-4a50-adf8-b121c8b52699/image.png)
