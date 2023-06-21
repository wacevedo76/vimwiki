--------------------------------------------------------------------------------
= PostgreSQL =
--------------------------------------------------------------------------------
  Send query to remote       | psql postgres://{user}:{password}@{ipaddress:port}/{database name} - c "Query String"
  server                     |
                             | example:
                             |      postgres://demo:secure_password@18.191.34.126:80/sample - c "SELECT count(ID) FROM employees;'
                             |
