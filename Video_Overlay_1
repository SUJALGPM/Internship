const express = require("express");
const colors = require("colors");
const morgan = require("morgan");
const cors = require('cors');
const dotenv = require("dotenv");
const connectDB = require("./config/db");
const sharp = require('sharp');
const path = require('path');
const { exec } = require('child_process');

//dotenv config
dotenv.config();

//Mongodb connection
connectDB();

//Rest object...
const app = express();

//Middlewares...
app.use(cors());
app.use(express.json());
app.use(morgan("dev"));

//routes...

//port...
const port = process.env.PORT || 8050;

// Specify the correct path to ffmpeg executable (update with your actual path)
const ffmpegPath = "S:\\COMPILER\\FFmpeg\\ffmpeg-master-latest-win64-gpl\\bin\\ffmpeg";

// File paths corrected using the assignment operator (=)
const inputVideoPath = './data/tamp.mp4';
const imageOverlayPath = './data/add2.jpg';
const outputVideoPath = './data/outputVideo19.mp4'; // Provide the full path including the filename

// Listen port...
const server = app.listen(port, () => {
    console.log(
        `Server Running in ${process.env.NODE_MODE} Mode on port ${process.env.PORT}`
            .bgCyan.white
    );

    // Additional code for video editing can be added here...
    const ffmpegCommand = `"${ffmpegPath}" -i "${inputVideoPath}" -i "${imageOverlayPath}" -filter_complex "overlay=10:10" "${outputVideoPath}"`;

    exec(ffmpegCommand, (error, stdout, stderr) => {
        if (error) {
            console.error(`Error: ${error.message}`);
            return;
        }
        console.log('Video successfully created with overlay:', outputVideoPath);
    });
});
