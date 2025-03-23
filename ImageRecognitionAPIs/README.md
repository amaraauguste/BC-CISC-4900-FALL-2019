# Image Recognition API Evaluator

The **Image Recognition API Evaluator** is a tool designed to evaluate the image labeling capabilities of various computer vision API vendors using Gaurav Oberoi's open-source tool, **Cloudy Vision**. You can find the Cloudy Vision repository [here](https://github.com/goberoi/cloudy_vision). This evaluator leverages the Apache Commons IO library for file operations and JFreeChart for visualizing statistical data.

## How It Works / Usage

### Prerequisites
1. **Run Cloudy Vision**: Start by running `cloudy_vision.py`.
2. **Record Results**: For each API you are evaluating (such as AWS Rekognition, Clarifai, IBM Watson, etc.), record the results in separate text files following this format:
   ```
   image_filename list_of_tags
   ```

### File Organization
- **API Results**: Save each API’s results in individual `.txt` files located in the `vendors` folder. If you're using Notepad, remember to deselect 'Word Wrap' under the 'Format' menu.
  
- **Image Filenames**: Compile a list of image filenames to be evaluated in a file named `image.txt`.

- **Manual Evaluation**: Collect the tags you want the APIs to be compared against and store them in the `info` folder.

- **Manual Results**: Record the results from your manual evaluation in a file named `manualResults.txt`, following the same format as the API tags:
   ```
   image_filename list_of_tags
   ```
  Again, ensure to avoid using duplicate terms and function words (like a, an, the, etc.) in your tag lists.

### Evaluation Process
1. **Data Parsing**: The evaluator reads data from each vendor's `.txt` file and saves it as an `API` object, containing `imageList` and `tags` arrays (handled in `API.java`).
2. **Comparison**: It compares the tags from manual evaluations to those provided by each API, calculating accuracy as a percentage.
3. **Ranking**: If more than one API is evaluated, the tool ranks them based on descending accuracy and identifies the most and least accurate APIs.
4. **Statistics**: The evaluator computes accuracy percentages and the average number of tags provided per image for each API, generating bar charts as visual representation. The charts are saved in the `images` folder as `percentageChart.png` and `averageChart.png`.
5. **Output Files**: All results are compiled into `output.txt` and `output.html`, formatted using the `template.html` file.

## Updates

### 04_14_2020: ImageRecognitionAPIs.java
- **Customizable Output**: Added functionality for customizable output file names or set directions to use default names (`output.txt` and `output.html`).
- **Duplicate Removal**: Implemented a `removeDuplicates` method that converts the string of tags from manual evaluations into a `LinkedHashSet`, effectively removing duplicate terms before reconversion to a `String[]` array for final output.

---
For detailed instructions on how to install dependencies or set up your environment, please refer to the official Cloudy Vision repository documentation.
