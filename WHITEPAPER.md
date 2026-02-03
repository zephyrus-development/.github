# Nexus CLI Whitepaper
The goal of the Nexus CLI project is to create a simple, easy to use interface that allows users to store and retrieve files on any device in a secure and efficient manner.

## Use Cases
1. A user needs to transfer a file from their laptop to their desktop PC.
2. A sysadmin that needs to run setup scripts on many new computers.
3. A user that wants to store files or notes securely
## Security
The `.config/key` file added to the repository after being encrypted by the provided password using AES encryption, this key is then downloaded and decrypted client side when a user needs to connect to the database.

The `.config/index` file is a json database in the following format, which has been aes encrypted using the same password as before, it is downloaded and decrypted client side to allow the user to find the names and locations of there files, the folders only exist in this database and all real files are stored unorganised with 16 random characters as the name and no file extension.
```json
{
	"note.txt": {
		"type": "file",
		"realName": "jbCr6vqgR1BtmMES",
	},
	"images": {
		"type": "folder",
		"contents": {
			"image.png": {
				"type": "file",
				"realName": "y0pg8IZuMYzfPmRQ",
			},
		},
	},
}
```

The `.config/publicIndex` file is a unencrypted json database similar to the first however it is not encrypted and the contents of the files specified in it are not encrypted either.
## How it works
### Part One: Setup
In order for the user to setup there personal file storage, they must first create a repository on GitHub named `.nexus`, this repository acts as server for there storage.

Next the user must generate a [deploy key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys) for the repository, using a newly generated ssh key, this key is going to be used to allow the nexus program to interact and add data to the repository. Once the key has been generated, and the public component of the key has been added to the repository settings, we must encrypt and upload the private key to a `.config/key` file in the repository, this can be done with the `nexus-cli setup <username> <path-to-private-key>` command, which will ask for a password for the vault, this is not recoverable so make sure to remember it or risk loosing your data, once this is completed successfully the nexus vault is operational.
### Part Two: Usage
Now the vault is setup we need to connect to it, this can be done inside of the specific retrieval or send command, however for ease of use it is recommended to connect to it if you wish to use it for more than one action. To connect use the command `nexus-cli connect <username>` you will then be prompted for the password, and if that is correct you will be connected to your vault, removing the requirement to login on every command. To disconnect use command `nexus-cli disconnect`, please note connection information is stored encrypted in the `nexus.conf` file in the directory of the nexus-cli application.

Indexing the vault, every vault contains a `.config/index` file, which is an encrypted register of filenames and locations, to read this index use the command below:
```sh
nexus-cli index # Prints the files and folders in the base directory of the vault
nexus-cli index images # Prints the files and folders in the images directory of the vault
nexus-cli search note # Prints the names, locations, and  of all the files with note in the name
nexus-cli search .txt # Prints the names and locations of all the files with extension .txt
```

Now the vault has been setup on the desired user account, the commands `retrieve` (can be shortened to `r`) and `upload` (can be shortened to `u`) can be used to send and retrieve files from the vault, examples are below.
```sh
nexus-cli retrieve image.png #retrieves the image.png file from the vault.
nexus-cli upload note.txt #encrypts and uploads the note.txt file to the vault.
```

Nexus-cli also gives users the option to upload a file publicly, in this case, a new unencrypted index called `publicIndex` in the `.config` folder, the commands related to this functionality are below.
```sh
nexus-cli connect <username> --public # Connect to a vault without authorisation to view public files
nexus-cli index #Reads the public files in the vault
nexus-cli retrieve text.txt #Download a public file.
```