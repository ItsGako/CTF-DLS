
# CTF Challenge: Maersk 🚢

## Description
The challenge revolves around industrial espionage involving a Docker image from a competitor of Maersk. The task is to extract a hidden flag from the Docker container using forensic techniques. This challenge is worth **100 points**! 🎯

## Steps Taken

1. **Pulling the Docker Image**:
   First, I executed the command to pull the Docker image from the public repository:
   ```bash
   docker pull fvln/decipher-flag
   ```

2. **Exploring the Docker Image**:
   To inspect the layers of the Docker image and identify files of interest, I used the `dive` tool:
   ```bash
   dive fvln/decipher-flag
   ```
   - I found that the image contained multiple layers, and I was particularly interested in the fifth layer, where files like `cleartext_flag.txt` and `decipher.sh` were located.

3. **Accessing the Layer**:
   After realizing the `decipher.sh` script was not available in the container, I needed to extract the files from the layer. I saved the Docker image to a tar file:
   ```bash
   docker save -o decipher-flag.tar fvln/decipher-flag
   ```

4. **Extracting the Layer**:
   I extracted the tar file to access its contents:
   ```bash
   tar -xvf decipher-flag.tar
   ```
   - I found a directory corresponding to the layers, and specifically targeted the layer containing `cleartext_flag.txt`:
   ```bash
   tar -xf /home/gako/7db0a850bd5757b09c66f9bedf7d1b10900508d8b21a732930ffd2d81289190e/layer.tar -C maersk
   ```
   - This extracted the contents into a folder named `maersk`, where I found the `/data` directory.

5. **Retrieving the Flag**:
   Inside the `/data` directory, I found the `cleartext_flag.txt` file. I displayed its contents using:
   ```bash
   cat /data/cleartext_flag.txt
   ```
   - The flag revealed was: **CTF{Beware_of_devops!}** 🎉

## Conclusion
This challenge showcased the importance of forensic analysis and the ability to extract hidden information from Docker images. It required patience and problem-solving skills to navigate through layers and files effectively. 🚀

---
*Flag found: CTF{Beware_of_devops!}*
