

# SQL 예시

RLS policy 모두 확인하기
```sql
select *
from pg_policies;
```


특정 테이블(instruments) RLS policy 확인하기
```sql
select *
from pg_policies
where tablename = 'instruments';
```

anon 과 authenticated 모두에게 RLS 허용하기
```sql
drop policy if exists "public can read instruments"
on public.instruments;

create policy "everyone can read instruments"
on public.instruments
for select
to anon, authenticated
using (true);
```

user 에게 phone4 컬럼 추가하기(auth 스키마는 대시보드에서 read-only 이므로 sql 으로만 수정가능)
```
alter table auth.users
add column phone4 text;
```


public.users 테이블 삭제하기
```
drop table public.users;
```