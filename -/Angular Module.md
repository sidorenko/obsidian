#angular 
Создание нового модуля в Angular - это простой процесс, который может быть выполнен вручную или с помощью Angular CLI. 

Создать новый модуль можно вручную следующим образом:

1. Создайте новый файл с расширением `.ts`. Название файла обычно соответствует названию модуля, например `my-module.module.ts`.
2. В этом файле создайте новый класс и декорируйте его с помощью `@NgModule`:

```typescript
import { NgModule } from '@angular/core';

@NgModule({
  declarations: [],
  imports: [],
  providers: [],
  exports: []
})
export class MyModule { }
```

Использование Angular CLI упрощает этот процесс и автоматически генерирует файлы и конфигурацию:

```
ng generate module my-module
```

Или сокращенно:

```
ng g m my-module
```

Эта команда создаст новый каталог с именем `my-module` и внутри него файл `my-module.module.ts` с базовой конфигурацией модуля. Если вам нужны маршруты в этом модуле, вы можете использовать флаг `--routing`.

```
ng g m my-module --routing
```

Теперь у вас есть готовый модуль, к которому вы можете добавлять компоненты, сервисы и другие Angular функции.