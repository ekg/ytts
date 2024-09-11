# YTTS (Your Text-to-Speech)

YTTS is a bash script that converts text files to speech using OpenAI's Text-to-Speech API. It splits large text files into smaller chunks, processes them in parallel, and combines the resulting audio files into a single output.

## Prerequisites

- Bash shell
- curl
- jq
- ffmpeg
- An OpenAI API key

## Installation

1. Clone this repository or download the `ytts` script.
2. Make the script executable:
   ```
   chmod +x ytts
   ```
3. Set your OpenAI API key in one of two ways:
   a. Create a file `~/.ytts/key` with the following content:
      ```
      export YTTS_API_KEY="your-api-key-here"
      ```
   b. Or, set it as an environment variable:
      ```
      export YTTS_API_KEY="your-api-key-here"
      ```

## Usage

Basic usage:
```
./ytts [options] <input_file> [output_file]
```

Options:
- `-h, --help`: Show the help message and exit
- `-v, --voice VOICE`: Specify the voice to use (default: alloy)
- `-s, --speed SPEED`: Specify the speech speed (default: 1.0, 2.0 for double speed)

If the output file is not specified, it defaults to `<input_file>.mp3`.

Examples:
```
./ytts input.txt
./ytts -v nova input.txt output.mp3
./ytts -s 1.5 input.txt fast_output.mp3
```

## Configuration

You can modify the following variables in the script to adjust its behavior:

- `MAX_CHUNK_SIZE`: Maximum size of text chunks (default: 1000 characters)
- `MAX_CONCURRENT_JOBS`: Maximum number of parallel jobs (default: 8)

## Supported Voices

The script supports all voices provided by OpenAI's Text-to-Speech API. As of the last update, these include:
- alloy (default)
- echo
- fable
- onyx
- nova
- shimmer

## Troubleshooting

1. If you encounter an error about the API key not being set, make sure you've either:
   - Created the `~/.ytts/key` file with your OpenAI API key, or
   - Exported the `YTTS_API_KEY` environment variable with your OpenAI API key.

2. If you're having issues with ffmpeg, ensure it's installed and accessible in your system's PATH.

3. For any other issues, check the error messages and ensure all prerequisites are installed correctly.

## License

This project is open-source and available under the MIT License.
