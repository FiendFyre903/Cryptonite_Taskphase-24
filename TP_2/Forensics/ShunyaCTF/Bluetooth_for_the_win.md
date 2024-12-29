# Bluetooth for the win

**Flag:** `0ctf{BLE_FTW}`

### How to solve

Using wireshark I analysed the requests and repsonses. As the description mentioned fidgeting and jaap hartsen is the inventor of bluetooth, I looked into the available bluetooth devices in the wireless section and found an audio device called `ear`. The requests also had a lot of volume changes in small time differences, which is what the fidgeting probably mentioned. I tried decoding it, and morse code was the solution, taking volume ups as `-` and volume downs as `.`, i got the following - `-… .-.. . .. — .- ..-. — . —` which translates to `BLE_FTW`

**What I learned:**

1. Using wireshark to a small degree

**Other incorrect methods I tried:**

- None

**References**

- None


