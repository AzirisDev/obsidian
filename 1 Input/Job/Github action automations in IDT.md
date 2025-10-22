### Adding iOS device to the project
Go to `developer.apple.com` -> 'Certificates, Identifiers & Profiles' -> Devices -> add the device of a user.

Now we need to update the profile.
- In `IDT Global Processing Services` - we go to `Boss Revolution Prod AdHoc`
- In `IDT Messaging Oy` - we go to `Boss Revolution Dev`

Edit the profile, choose necessary certificates, remove mac access, choose all devices in device-list. Download the profile.

Go to terminal:
- `base64 -i downloaded_profile -o output_file` - turn profile to base64 format
- `cat output_file | pbcopy` - copy the content into buffer
- go to secrets and replace the profile secrets in github actions.

### Adding user to Firebase app distribution
`Run -> App Distribution -> Testers & Groups -> add user by email`
If user does not receive the invitation:
`Go to any build -> Testers -> resend the invitation`


### Update apple certificates

##### 1. Generate a Certificate Request (CSR)
1. Open **Keychain Access** on your Mac.
2. From the menu, go to:  
    **Keychain Access → Certificate Assistant → Request a Certificate from a Certificate Authority...**
3. Enter your Apple Developer email and Common Name (e.g., _Azim Developer_).
4. Choose **Saved to disk** (not emailed).
5. This creates a `.certSigningRequest` file.

##### 2. Create the Certificate on Apple Developer
1. Go to Apple Developer Certificates.
2. Choose the appropriate type:
    - **Apple Distribution** (for App Store builds)
    - **Apple Development** (for testing)
3. Upload the `.certSigningRequest` file you generated.
4. Download the created certificate (`.cer` file).

##### 3. Import and Export the Certificate with Private Key
1. Double-click the `.cer` file to import it into **Keychain Access**.
2. Verify that both the certificate and its **private key** appear in the _login_ keychain.
3. Right-click the certificate → **Export**.
4. Save as a `.p12` file and set a **strong password** (you’ll need this later).

##### 4. Encode the Files in Base64
To safely store in GitHub Secrets, convert the `.p12` files into base64 strings:
- `base64 -i Certificates.p12 | pbcopy`

Add certificate and password to the github action secrets.

### People to connect
- if it is trouble with running machine - @yulyan.glonti

