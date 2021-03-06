Django ORM

- lazy QuerySet
  - 쿼리셋을 생성하는 작업이 DB 에서의 작업을 의미하지 않는다. DB Query 는 실제로 장고 쿼리셋의 값을 불러올 때 연산한다. filter 를 사용해도 마찬가지다. 
- 쿼리셋 캐싱(caching)
  - 만약 연산된 쿼리셋을 다시 실해한다면 그 전에 실행해서 메모리에 캐리된 값이 나오게된다. DB 의 쿼리문을 실행하지 않는다.
  - 만약 Post.objects.all() 값들이 이미 리스트에 담겨있다면 post.title 은 캐싱된 값을 사용한다.
- 캐싱이 사용되지 않을 때
  - 만약 쿼리셋의 일부만 연산될 경우, slicing 이나 index , 라면 캐시값을 확인하긴하지만 결과값을 새로 캐시하지 않는다.
    - p = Post.objects.all() 의 경우
    - p[5] 를 실행한다면 실행할때마다 DB 쿼리가 실행되게 된다. 
- ORM 을 효율적으로 작성하기
  - foreign key
    - all() 로 불러오는 것이 아니라 objects.select_related('key').all() 로 불러오기
  - many to many
    - prefech_related()
  - values(), value_list()
    - 객체가 필요하지 않은 경우, 값만 필요한 경우
  - difer(), only()
    - 사용하지 않는 컬럼은 가져오지 않는다. only() 는 사용하는 컬럼만 가져옴
  - exists(), count()
    - 'if 쿼리셋' 이 아닌 if 쿼리셋.exists() 를 사용하자 
- django debug toolbar 를 사용해서 쿼리셋의 중복을 확인해보자