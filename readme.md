LOKI_URL="http://your-loki-instance:3100/loki/api/v1/push"
USERNAME="your_username"
PASSWORD="your_password"
TIMESTAMP="1634890269000000000"
LOG_DATA="{\"name\":\"John Doe\",\"score\":95,\"address\":\"123 Main St\",\"gender\":\"Male\",\"phone\":\"123-456-7890\",\"income\":50000}"
LABELS="{\"job\":\"test-job\",\"instance\":\"localhost\"}"

curl -X POST "$LOKI_URL" \
     -H "Content-Type: application/json" \
     -u "$USERNAME:$PASSWORD" \
     -d "{
           \"streams\": [
             {
               \"stream\": $LABELS,
               \"values\": [ [\"$TIMESTAMP\", \"$LOG_DATA\"] ]
             }
           ]
         }"
