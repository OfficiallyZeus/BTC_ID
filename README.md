store_name="My awesome store"
body="$(echo "{}" | jq --arg "a" "$store_name" '. + {name:$a}')"
store_id="$(curl -s \
     -H "Content-Type: application/json" \
     -H "Authorization: token $apikey" \
     -X POST \
     -d "$body" \
     "$BTCPAY_INSTANCE/api/v1/stores"  | jq -r .id)"
