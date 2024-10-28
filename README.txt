



Device: JETSON ORIN AGX

1. Information about the System OS:
   command: cat /etc/os-release

details: 


NAME="Ubuntu"
VERSION="20.04.6 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.6 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal


2. Install JETPACK SDK
   command: sudo apt install nvidia-jetpack -y

details: 
nvidia-jetpack is already the newest version (5.1.2-b104)

3. Develop the python virtual environment for running the scripts:
   command: python -m venv compressai_env
   command to activate: source compressai_env/bin/activate
   
   command to install the modules: pip install -r requirements.txt
    
   This will not install the TensorRT as the TensorRT wheels for the ARCH linux 
   version are not present.
  
   Solution: Link the TensorRT module installed using the JETPACK with the 
   virtual environment.

   1. Find the library in the system (Not in the virtual environment)
      command: sudo find /usr -name "*tensorrt"
      output: /usr/lib/python3.8/dist-packages/tensorrt

   2. then go to the virtual environment path 
      "/home/swapnil09/compressai_env/lib/python3.8/site-packages/

   3. thenk link it
      ln -s /usr/lib/python3.8/dist-packages/tensorrt/ .


4. Now check the tensorrt
   command: python 
	    import tensorrt as trt
            print(trt.__version__)
   output: this should print the tensorrt version
   8.5.2.2 

 



