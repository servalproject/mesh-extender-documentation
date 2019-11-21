# Flashing a Gl-AR150-based Mesh Observer

1. **Connect an Ethernet cable** between the AR150's WAN port and your computer
2. Configure your Ethernet interface to use the IP `192.168.1.2`
3. Hold the reset button down on the AR150
4. Connect power to the AR150 while still holding the reset button
5. Let go of the reset button *on the 6th blink* of the red light (the centre green light should illuminate as the red one does)

After releasing the reset button, the red light should blink rapidly for about a second. If not, and instead both green LEDs are lit, then you must have released the reset button too early or too late. Disconnect power and repeat steps 3-5 again.

6. Open [http://192.168.1.1](http://192.168.1.1) in your browser
7. Click 'Choose file' and select the firmware file
8. Click 'Update firmware'
9. Wait for the upload to complete and the router to reboot automatically

The firmware should have been successfully flashed
