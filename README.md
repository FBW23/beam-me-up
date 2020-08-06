## Mini Fullstack App - the magic file

Please create a little app with frontend & backend to upload & display a file.

### Frontend for uploading an image file

- Code a little form with file input button and submit button
- Setup state to store the file: const [file, setFile] = useState()
- Add an onChange handler to store the file input: 
    - Hint: onChange={ (e) => setFile( e.target.files[0] ) }
- onSubmit: 
    - Send the data to your backend using FormData
        - This way we can also send files using fetch / axios
    - Hints for sending file with fetch: 
        - `let formData = new FormData()`
        - `formData.append("my_file", file)` // use that name "my_file" in your multer middleware later!
        - `fetch('/someRoute', { method: "POST", body: formData })`

### Backend for storing your image

- Setup Multer for receiving files into a directory “/uploads”
- Setup an express POST route /upload
- Attach multer middleware to route /upload
    - Hint: upload.single('my_file') // => use here the same name you used in your frontend
- Send the name of the stored file back to the frontend

### Testing

- Start your backend
- Call it from the frontend using your file upload form
- Test if you receive the uploaded file in the backend
- Test if you get back the filename in the frontend

#### Bonus - Display file in frontend

Now we want to provide a route in the frontend to display the uploaded backend file.

- Adapt Backend: 
    - Share /upload folder with express.static

- Adapt Frontend: 
    - After upload: Store received filename in localStorage
    - Create a route /file
        - Display here the stored image using an img tag
        - Hint: Set as URL to the file the domain of the backend + stored filename
    - Adapt upload form: Redirect to route /file after upload
    - Test if the uploaded file is displayed
    - Show also the filename in some heading tag

Well done! 

Now you can store all sorts of data, including JSON, images, movies, etc, in a backend and make use of it in a frontend. We reached a huge milestone.
