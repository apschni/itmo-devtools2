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

### 4.  Используем `git blame` и находим 32 строчку:
```
git blame prisma/seed.ts
```
![image](https://user-images.githubusercontent.com/64983176/197629469-f3a40f9f-8ae2-440b-9a81-8c34fee2da2d.png)

### 5. Используем `git bisect`, помечая ребочие коммиты как `bisect bad`, нерабочие - `bisect bad`, пока не найдем `first bad commit`.
![image](https://user-images.githubusercontent.com/64983176/197629479-c291b1b5-73a1-4601-9768-2737676d9fa8.png)

### 6. С помощью `filter-branch` удалим `.env` из всех коммитов, затем добавим в `.gitgnore`:
```
git filter-branch --tree-filter "rm -f .env" -- --all
echo .env >> .gitignore
```
![image](https://user-images.githubusercontent.com/64983176/197629492-fb10cdbd-1c0a-4c77-956b-f186390ea799.png)

### 7. Изменим автора коммитов:
![image](https://user-images.githubusercontent.com/64983176/197629498-0ceef320-45a0-4975-95f3-f7153151e5c5.png)
![image](https://user-images.githubusercontent.com/64983176/197629505-d51ebe7a-4182-4ada-bd3c-a2f5457b98b2.png)

### 8. Используя запоминание разрешений конфликтов вмерджим `feature` в `master`, разрешив конфликт при слиянии. Откатим слияние, внесем изменение в файл `README.md` и снова влейте ветку `feature` в `master`
```
git checkout master
git config rerere.enabled true
git merge feature
```

```
git add *file-name*
git commit --no-edit
git reset --hard HEAD~1
git merge feature
```