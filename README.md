# send a payment to Blockonomics.co through their API using PHP

1.Generate an API key: You will need an API key to use Blockonomics.co API. You can generate an API key by logging in to your Blockonomics account and navigating to the API tab.

2.Set up your PHP code: You can use PHP's cURL library to interact with Blockonomics.co API. Start by creating a new PHP file and including the cURL library.

3.Create a payment request: To create a payment request, you will need to send a POST request to Blockonomics.co API endpoint. The payment request should include the amount you want to receive, your Bitcoin address, and your API key.

Here is an example of how to create a payment request using PHP:

```
$url = "https://www.blockonomics.co/api/new_address";
$apiKey = "YOUR_API_KEY";
$address = "YOUR_BITCOIN_ADDRESS";
$amount = "AMOUNT_TO_RECEIVE";

$data = array(
    "api_key" => $apiKey,
    "address" => $address,
    "amount" => $amount
);

$options = array(
    CURLOPT_URL => $url,
    CURLOPT_POST => true,
    CURLOPT_POSTFIELDS => http_build_query($data),
    CURLOPT_RETURNTRANSFER => true,
);

$curl = curl_init();
curl_setopt_array($curl, $options);
$response = curl_exec($curl);
curl_close($curl);

echo $response;
```
Replace "YOUR_API_KEY", "YOUR_BITCOIN_ADDRESS", and "AMOUNT_TO_RECEIVE" with your own values.

Handle the payment response: Once you send the payment request, you will receive a response from Blockonomics.co API. The response will include a payment URL and a Bitcoin address where the user can send the payment. You can use this information to display a payment button or QR code to the user.
Here is an example of how to handle the payment response using PHP:

```
$response = json_decode($response, true);

if ($response["status"] == "success") {
    $paymentUrl = $response["payment_url"];
    $bitcoinAddress = $response["address"];

    // Display payment button or QR code
} else {
    $errorMessage = $response["message"];

    // Display error message
}

```
This code checks if the payment request was successful or not. If it was successful, it extracts the payment URL and Bitcoin address from the response and displays a payment button or QR code to the user. If it was not successful, it displays an error message to the user.
