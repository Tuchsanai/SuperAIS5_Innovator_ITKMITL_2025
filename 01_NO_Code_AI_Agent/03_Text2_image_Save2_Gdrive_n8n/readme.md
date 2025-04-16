
'''

## Models URL
 https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp-image-generation:generateContent


## Prompt

...

Create a highly detailed and visually stunning image based on the following text description:  {{ $json.chatInput }} The image should capture the essence, mood, and specific details described in the text. Use vibrant colors, realistic textures, and appropriate lighting to bring the scene to life. Ensure the composition is balanced and visually appealing.

[CONSIDER]
- prompt in English only.
- no "", '', in prompt.
- display prompt only not describe.

'''



## json form Google AI Studio
{
  "contents": [
    {
      "role": "user",
      "parts": [
        {
          "text": "{{$json.output.replace(/[\r\n]+/g, ' ')}}"
        }
      ]
    }
  ],
  "generationConfig": {
    "responseModalities": ["Text", "Image"]
  }
}

##