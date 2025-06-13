### 1. Исследование объекта blob
Output:  
just some text  
and another one  
and one more line  
  
Blob хранит содержимое файла. Важно, что при изменении файла создается новый blob  
  
### 2. Исследование объекта tree
Output:  
100644 blob af7fda8ea32b60578a1103ce061a50d7f6f09a35    README.md  
100644 blob 7a94f7af59b8968be392288ea03179a24ffc9d9e    lab1.md  
100644 blob 77e299c4cdb01bc31607bef4e2036b56c3368515    lab2.md  
100644 blob 33e58253294a87c666b264274a4759d6cc4c9b4a    task1.md  
100644 blob bdacd7855b0b5faaa845cbceac4a999aa7a35b51    text.txt  
  
Tree хранит структуру каталогов. Запись содержит права доступа к файлу, тип и хеш объекта, имя файла или директории.  

### 3. Исследование объекта commit
Output:  
tree c8e935f996448b2b0ea1695a1f584b7267c4f6e3  
parent 8b71951db2603e5ed7d0d594e8e2bc58eacbaae7  
author kotosham <mishzlata@gmail.com> 1749848912 +0300  
committer kotosham <mishzlata@gmail.com> 1749848912 +0300  
gpgsig -----BEGIN SSH SIGNATURE-----  
...  
 -----END SSH SIGNATURE-----  
update text file  
  
Commit - состояние репозитория в определенный момент. Содержит ссылку на tree, родительский commit, информацию об авторе и времени, содержимое коммита.