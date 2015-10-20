Для начала надо добавить анализатор в индекс для поиска по email
[source,json]
-------------------------
PUT /portal {
"settings": {
  "analysis": {
    "filter": {
      "email": {
        "type": "pattern_capture",
        "preserve_original": 1,
        "patterns": [
          "([^@]+)",
          "(\\p{L}+)",
          "(\\d+)",
          "@(.+)",
          "([^-@]+)"
        ]
      }
    },
    "analyzer": {
      "email": {
        "tokenizer": "uax_url_email",
        "filter": [
          "email",
          "lowercase",
        ]
      }
    }
  }
}
}
-------------------------
