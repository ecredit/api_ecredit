# Партнерское API eCredit

## Формат вызова

## Версионирование

## Общие для всех методов параметры

Имя | Описание
--- | ---
method | Имя метода
user_id | ID пользователя
user_flag | Тип нумерации пользоваеля
client_id | ID дилера
signature | Авторизационная подпись

Каждый запрос выполняется в связке дилер (client_id) + пользователь (user_id), который имеет доступ к указанному дилеру. При этом user_id пользователя может быть задан по нумерации еКредит (в этом случае параметр user_flag=0 или не задан) или по нумерации дилера (user_flag=1)

Параметр signature высчитывается как "соль" от передаваемый данных, подписанная секретным ключом и вычисляется по такому алгоритму:

```
`$signature = base64_encode(hash_hmac("sha1", json_encode($params), "xxxxxx", $raw_output = true))
```
где: 

$params - тело запроса, полезная нагрузка от каждого конкретного метода

xxxxxx - секретный ключ
