// Import the tesseract.js library, which allows to recognize text from images

const teser =require('tesseract.js');

// Call the recognize method, which takes three arguments: the path to the image, the language of the text and an object with settings

teser.recognize('./ai_cbr_2-min.png','rus',{

    // In the settings, specify a function logger, which will be called at each stage of recognition and receive an object with information about the progress
    logger: e=>{
    
        // Log the object with information about the progress to the console
        
        console.log(e)
    }
})

    // After the recognition is completed, the recognize method will return a promise, which we handle with the then method
    .then(out=>{
        // Get the recognition result as an object out, which has a property data with data about the text
        // Extract the text from the data.text property and assign it to the variable text
        let text = out.data.text
        // Replace all line breaks in the text with spaces using the replace method and a regular expression /\n/g
        .replace(/\n/g, ' ')
        // Replace all characters except letters and numbers with an empty string using the replace method and a regular expression /[^a-zA-Zа-яА-Я0-9 ]/g
        .replace(/[^a-zA-Zа-яА-Я0-9 ]/g, '');
        // Log to the console the text "this is what I read:" and the variable text with the recognition result
        console.log('this is what I read:',text);
    })
