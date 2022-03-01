--------------------------------------------------------------------------------
= Parsing =
--------------------------------------------------------------------------------
== Parsing and Storing in Ruby ==
--------------------------------------------------------------------------------
=== CSV ===
==== Parsing CSV ====
  require 'csv'

  filepath = 'beers.csv'

  CSV.foreach(filepath) do |row|
    # Here, row is an array of columns
    puts "#{row[0]} | #{row[1]} | #{row[2]}"
  end

==== Parsing CSV (with Header row) ====
  require 'csv'

  csv_options = { col_sep: ',', quote_char: '"', headers: :first_row }
  filepath    = 'beers.csv'

  CSV.foreach(filepath, csv_options) do |row|
    puts "#{row['Name']}, a #{row['Appearance']} beer from #{row['Origin']}"
  end

==== Storing CSV ====
  require 'csv'

  csv_options = { col_sep: ',', force_quotes: true, quote_char: '"' }
  filepath    = 'beers.csv'

  CSV.open(filepath, 'wb', csv_options) do |csv|
    csv << ['Name', 'Appearance', 'Origin']
    csv << ['Asahi', 'Pale Lager', 'Japan']
    csv << ['Guinness', 'Stout', 'Ireland']
    # ...
  end

=== JSON ===
==== Parsing JSON ====
  Parsing JSON
  require 'json'

  filepath = 'beers.json'

  serialized_beers = File.read(filepath)

  beers = JSON.parse(serialized_beers)
  # JSON.parse(serialized_beers) returns a Ruby Hash

==== Storing JSON ====
  require 'json'

  beers = { beers: [
    {
      name:       'Edelweiss',
      appearance: 'White',
      origin:     'Austria'
    },
    {
      name:       'Guinness',
      appearance: 'Stout',
      origin:     'Ireland'
    },
    # etc...
  ]}

  File.open(filepath, 'wb') do |file|
    file.write(JSON.generate(beers))
  end

