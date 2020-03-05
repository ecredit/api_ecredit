# Редактировать список дилеров, к которым пользователь имеет доступ

Имя метода `Request_EditUserAccess`

## Список параметров
Авторизационный пользователь
Изменяемый пользователь
Список дилеров

Если `change_dealer_id` не будет задан, то метод вернет список дилеров, к которым имеет доступ изменяемый пользователь
```
{
  "error_code":200,
  "error_text":"Ok",
  "id":"5e60be6569d2e",
  "response":{
      "dealers":[
          {
            "ecredit_dealer_id":155,
            "dealer_id":null
          },
          {
            "ecredit_dealer_id":158,
            "dealer_id":null
          },
          {
            "ecredit_dealer_id":437,
            "dealer_id":null
          }
        ],
        "count_added":0,
        "not_valid_dealers":{}
  }
}
```

## Ограничения
Авторизационный пользователь должен иметь иметь доступ к каждому из указанный дилеров в параметре `change_dealer_id`. Те дилеры, к которым авторизационный пользователь не имеет доступа, не будут добавлены к изменяемому пользователю. Список таких дилеров будет в ответе метода в поле `not_valid_dealers`

[Особые ограничения для авторизационного и изменяемого пользователя](additional_user_condition.md)

## Пример ответа метода
```
{
  "response": {
    "dealers": [
      {
        "ecredit_dealer_id": 155,
        "dealer_id": null
      },
      {
        "ecredit_dealer_id": 437,
        "dealer_id": null
      }
    ],
    "count_added": 2,
    "not_valid_dealers": [
      "158",
      "318"
    ]
  },
  "error_code": 200,
  "error_text": "Ok",
  "id": "5e60be6569d2e"
}
```

