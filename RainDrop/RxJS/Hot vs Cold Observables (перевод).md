---
raindrop_id: 533067785
raindrop_last_update: 2023-03-12T23:57:30.600Z
---

# Metadata
Source URL:: https://medium.com/@aksenovdev/hot-vs-cold-observables-%D0%BF%D0%B5%D1%80%D0%B5%D0%B2%D0%BE%D0%B4-4951ee651e4c


---
# Hot vs Cold Observables (перевод)

Перевод статьи Ben Lesh “Hot vs Cold Observables“

## Highlights

> [!quote]+ Updated on 2023/03/10 18:58:22
>
> Producer — это источник значений для вашего observable.

> [!danger]+ Updated on 2023/03/10 19:00:16
>
> Итак, всё, что подпишется на source выше получит свой собственный экземпляр соединения Websocket, и при закрытии произойдёт .close() подключения. Это означает, что наш источник действительно одноадресный, потому что producer может посылать значений только одному observer.
