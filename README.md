# IPFS Video Uploader

This is an alternative IPFS uploader to upload videos onto DTube. Includes a basic web UI.

### Dependencies required

* `npm` command line tools
* `ffmpeg`, `imagemagick` and `bc` for sprite generation
* `go-ipfs` with a running daemon

### Additional requirements

* A SteemConnect application
* A domain name for HTTPS, plus SSL certificate for that domain installed (code is written to work well with certbot)

# Installation

1. Clone this repository by typing `git clone https://github.com/techcoderx/ipfsVideoUploader.git` in a terminal window.

2. Intall all required node modules. `cd ipfsVideoUploader && npm install`

3. Configure uploader by modifying `config.json` file. If you need help with the configuration, view the documentation [here](https://github.com/techcoderx/ipfsVideoUploader/blob/master/ConfigDocs.md)

4. Run `node getLoginLink.js` to generate SteemConnect login link.

5. Replace the login link with the one you obtained from step 3 [here](https://github.com/techcoderx/ipfsVideoUploader/blob/master/client/welcome.html#L7).

6. If `whitelistEnabled` is set to `true`, add some Steem accounts to the whitelist by modifying [whitelist.txt](https://github.com/techcoderx/ipfsVideoUploader/blob/master/whitelist.txt). (one line per Steem user)

7. Run the app by typing `node index.js`. Your app will listen to port 80, and 443 if you have HTTPS enabled.

*Note: You may need to enable read permissions for `/etc/letsencrypt/live/yourdomain.com/` directory for the user account if using HTTPS; and port 80 and 443 binding permissions (or use a reverse proxy).*

All uploaded files will be saved in the `uploaded` folder within the repo.

# Supported file formats

IPFS works the best for videos with .mp4, therefore only mp4 files will be supported at this moment. Both .jpg and .png file formats are supported for thumbnail uploads.

Right now the uploader will only take source videos, but options for adding a user-encoded 240p, 480p, 720p and 1080p versions of the source video will be added later.

# GET API

To get usage info for specific Steem user:
```
/usage?user=STEEM_USERNAME
```
* `user` *(required)*: Steem account username

To get list of hashes of uploaded files:
```
/hashes?user=STEEM_USERNAME&hashtype=videos,thumbnails,sprites
```

* `user` *(optional)*: Steem account username
* `hashtype` *(required)*: Type of hash to obtain. Valid values: `videos`, `thumbnails`, `sprites`.

# How to contribute?

If you found any ways to improve on the code, or found any bugs, feel free to create a pull request on the GitHub repository. You can also contact me on Discord `techcoderx#7481` if you have any enquiries.