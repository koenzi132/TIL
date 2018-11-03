axios의 POST 기능을 구현하는 도중, 

submit 버튼을 누르면

데이터가 먼저 만들어지고 그것이 서버로 POST가 되게 만드는 부분이 있었는데,

><button type="submit" onClick={ () -> {
>
>​		this.makePostData();
>
>​		this.submitData();
>
>}}> 등록하기 </button>

이런식으로 만들었더니, 함수들의 complete 순서가 꼬이는지 오류가 발생해서

서버에 아무 데이터도 들어가지 않았다.

그러던 도중, **async 와 await** 에 대해 알게 되어 적용해보았더니 해결되었다.

**사용방법**은 다음과 같다. 

><button type="submit" onClick={async () => {
>
>​           	   await this.makePostData();
>
>​          	    await this.submitData();
>
>​            }}> 등록하기 </button>



<u>**async와 await의 작동 원리**는 다음과 같다.</u>

* async (동기함수 방식으로 작동하는 함수로 설정하는 것)
* await (해당 함수가 순서대로 작동하도록 설정하는 것)

**만드는 방법**은,

>makeData = **async** () => {
>
>}
>
>or
>
>var makeData = **async** function () {
>
>}

이런식으로 async 함수를 만들어주고,

**사용할 때**에는,

> **await** makeData();
>
> **await** nextFunc();

이런 식으로 사용하고자 하는 함수 순서대로 적어 사용한다.