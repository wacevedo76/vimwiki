--------------------------------------------------------------------------------
Curl
--------------------------------------------------------------------------------
  Post request (with body)   | curl -X 'POST' 'http://127.0.0.1:8000/cars' \
                             |   -H 'accept: application/json' \
                             |   -H 'Content-Type: application/json' \
                             |   -d '{"message": {
                             |   "brand": "FIAT",
                             |   "model": "500",
                             |   "year": "2015"
                             |   }
                             | }'
                             |
