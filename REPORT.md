## Отчет по лабораторной работе №2

### 1. Для визуализации был использован плагин Git Graph для VSCode
![image](https://user-images.githubusercontent.com/64983176/197629329-45fe6a03-869e-4ee4-a1b0-e11794285935.png)

### 2.  Используем `git rebase`:   
```
git checkout ci
git rebase -i HEAD~2
```
![image](https://user-images.githubusercontent.com/64983176/197629401-5bf868d7-57fb-4c40-b95a-2b55d65deeda.png)
![image](https://user-images.githubusercontent.com/64983176/197629430-09fba8a7-9cdd-4a95-9ccf-b1b10c99800d.png)
![image](https://user-images.githubusercontent.com/64983176/197629446-eebfd219-d99f-418d-afef-d78147787bb5.png)
### Далее делаем `cherry-pick` и удаляем ветку `ci`
![image](https://user-images.githubusercontent.com/64983176/197629459-83e40026-5f06-454b-9984-44de67e8d4e7.png)

### 3.  Используем `reflog`:
```
git reflog
git checkout aca3abb
git branch old-master
```
![image](https://user-images.githubusercontent.com/64983176/197629457-8481f9bf-7655-4011-8494-3c92380e2d38.png)