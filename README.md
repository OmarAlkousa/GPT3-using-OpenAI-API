# GPT3-using-OpenAI-API
Intergrating with Chat-GPT using OpenAI API in python.

## **Instructions:**

1- Sign up for [OpenAI](https://auth0.openai.com/u/signup/identifier?state=hKFo2SBvSy02UTZIXzJqSm1OREl2UnY5OTljc1haMl9mb21GdKFur3VuaXZlcnNhbC1sb2dpbqN0aWTZIFVyU1BZaDJhOGR0NUlSdU5PSENPOHJpcHVOWU5BRXFpo2NpZNkgRFJpdnNubTJNdTQyVDNLT3BxZHR3QjNOWXZpSFl6d0Q)

2- Generate your secret API-key using the api-key generator in this [link](https://beta.openai.com/account/api-keys)

3- Refer to this [Notebook](https://github.com/OmarAlkousa/GPT3-using-OpenAI-API/blob/68e0faf87d652abcc18c9f701a74f0bd0790a373/OpenAI_API_GPT3.ipynb) and paste your secret API-key into **my_api_key** variable.

4- You're ready to talk with Chat-GPT:)

## Examples:

```sh
# Recommendation for journals related to medical image processing
ask_gpt3('top 10 medical imaging processing journals... with impact factor')
```

```sh
1. IEEE Transactions on Medical Imaging (Impact Factor: 5.845)
2. Medical Image Analysis (Impact Factor: 5.717)
3. IEEE Journal of Biomedical and Health Informatics (Impact Factor: 4.845)
4. Computerized Medical Imaging and Graphics (Impact Factor: 4.717)
5. Medical Physics (Impact Factor: 4.637)
6. Physics in Medicine and Biology (Impact Factor: 4.541)
7. International Journal of Computer Assisted Radiology and Surgery (Impact Factor: 4.527)
8. Journal of Digital Imaging (Impact Factor: 4.521)
9. Medical Image Computing and Computer-Assisted Intervention (Impact Factor: 4.500)
10. IEEE Transactions on Biomedical Engineering (Impact Factor: 4.494)
```

**You can ask GPT for a code, for example:**

```sh
# code example that can apply a cosutmer filter in MATLAB
ask_gpt3('matlab code to apply a costume filter on a medical image')
```
```sh
% Read in the medical image
I = imread('medical_image.jpg');

% Create a custom filter
custom_filter = [1 2 1; 2 4 2; 1 2 1];

% Apply the custom filter to the medical image
filtered_image = imfilter(I, custom_filter);

% Display the filtered image
imshow(filtered_image);
```
**Example of longer answers, increasing "answer_length":**

```sh
# Build a network mesh of 6 esp8266 controllers
ask_gpt3('esp8266 code to do a wireless mesh network of 6 controllers', answer_length = 2000)
```

```sh
// Include the necessary libraries
#include <ESP8266WiFi.h>
#include <WiFiUdp.h>

// Set up the WiFi network
const char* ssid = "YourNetworkName";
const char* password = "YourNetworkPassword";

// Set up the mesh network
WiFiUDP udp;
IPAddress meshNetworkIP(192, 168, 0, 1);

// Set up the controllers
IPAddress controller1IP(192, 168, 0, 2);
IPAddress controller2IP(192, 168, 0, 3);
IPAddress controller3IP(192, 168, 0, 4);
IPAddress controller4IP(192, 168, 0, 5);
IPAddress controller5IP(192, 168, 0, 6);
IPAddress controller6IP(192, 168, 0, 7);

// Set up the ports
const int controller1Port = 80;
const int controller2Port = 81;
const int controller3Port = 82;
const int controller4Port = 83;
const int controller5Port = 84;
const int controller6Port = 85;

// Set up the message buffer
char messageBuffer[256];

void setup() {
  // Connect to the WiFi network
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.println("WiFi connected");

  // Set up the mesh network
  udp.beginMulticast(meshNetworkIP, controller1Port);
  Serial.println("Mesh network set up");
}

void loop() {
  // Receive messages from the controllers
  int packetSize = udp.parsePacket();
  if (packetSize) {
    int len = udp.read(messageBuffer, 256);
    if (len > 0) {
      messageBuffer[len] = 0;
    }
    Serial.println("Received message: " + String(messageBuffer));

    // Send the message to the other controllers
    udp.beginPacket(controller2IP, controller2Port);
    udp.write(messageBuffer);
    udp.endPacket();
    udp.beginPacket(controller3IP, controller3Port);
    udp.write(messageBuffer);
    udp.endPacket();
    udp.beginPacket(controller4IP, controller4Port);
    udp.write(messageBuffer);
    udp.endPacket();
    udp.beginPacket(controller5IP, controller5Port);
    udp.write(messageBuffer);
    udp.endPacket();
    udp.beginPacket(controller6IP, controller6Port);
    udp.write(messageBuffer);
    udp.endPacket();
  }
}
```

## Acknowledgment:
- OpenAI API Documentation, Libraries, [Python Bindings](https://beta.openai.com/docs/libraries/python-bindings) [Accessed at 11-Jan-2023]
- OpenAI API Documentation, Guides, [Text Completion](https://beta.openai.com/docs/guides/completion/introduction) [Accessed at 11-Jan-2023]
- OpenAI API Documentation, API Reference, [Authentication](https://beta.openai.com/docs/api-reference/authentication) [Accessed at 11-Jan-2023]
- OpenAI API Documentation, API Reference, [Create Completion](https://beta.openai.com/docs/api-reference/completions) [Accessed at 11-Jan-2023]
- OpenAI API Repository, [OpenAI Python](https://github.com/openai/openai-python.git) [Accessed at 11-Jan-2023] 
