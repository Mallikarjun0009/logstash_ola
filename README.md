input { tcp { port => 12000 } }
filter {
  csv {
    separator => ","
    columns => ["ID", "Timestamp", "Source_IP", "Destination_IP", "Protocol", "Length", "Message"]
  }

  # Optional: Parse the 'Message' field to extract individual key-value pairs
  kv {
    source => "Message"
  }
}
output { stdout { codec => rubydebug } }

