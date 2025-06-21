### Основные компоненты GitHub Actions:
1. **Workflow** - автоматизированный процесс, описываемый YAML-файлом;
2. **Job** - набор шагов, выполняемых на одном runner;
3. **Step** - отдельная задача (может быть командой или action);
4. **Action** - переиспользуемый компонент для упрощения workflow;
5. **Runner** - сервер, на котором выполняются jobs (GitHub-hosted или self-hosted).

### Порядок действий:
- создана папка .github/workflows в репозитории;
- добавлен файл workflow github-actions-demo.yml, использован пример из гайда;
- сохранен файл и создана новая ветка lab3.

### Результаты выполнения workflow:
> Set up job
> Run echo The job was automatically triggered by a push event."
> Run echo This job is now running on a Linux server hosted by GitHub!"
> Run echo The name of your branch is refs/heads/lab3 and your repository is kotosham/Sum25-intro-labs."
> Check out repository code
> Run echo The kotosham/Sum25-intro-labs repository has been cloned to the runner."
> Run echo The workflow is now ready to test your code on the runner."
> List files in the repository
> Run echo This job's status is success."
> Post Check out repository code
> Complete job
  
Ошибок не возникло, workflow занял 7 секунд, для каждого шага можно посмотреть логи.