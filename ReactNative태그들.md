## React Native Tags

> React Native에서 사용되는 유용한 태그들

- <ActivityIndicator> = 스피너를 생성해줌.
- <View> = React 에서의 <div> 태그와 같다고 보면 됨.
- <Text> = text를 넣고 싶을 때는 Text 태그로 감싸주어야 한다.
- <SafeAreaView> = The purpose of *SafeAreaView* is to render content within the safe area boundaries of a device. (현재 iOS version 11의 iOS 디바이스에서만 적용가능. 19/12/2018 기준)
- <ScrollView> = 현재 화면 컨텐츠들이 스크롤되도록 만들어줌. (상위 태그로 감싸줌)
- <FlatList> = map처럼 여러 가지 데이터들을 뿌려줄 때 사용함. Array로 데이터를 넣어주며, map으로 작업을 진행할 때보다 퍼포먼스가 좋다. (사진들을 뿌려주거나 할 때 이용하면 됨)
- <SectionList> = FlatList와 비슷하지만, 이건 카테고리들을 분류할 때 사용하면 유용. FlatList보다 퍼포먼스가 좋음.
  (Title / 소제목 등으로 이루어졌을 때 사용.)
  - ex ) **Guitar**
         - Base Guitar
            요런 식으로... 큰 카테고리 범주, 소범주 이런 식으로..?
- 