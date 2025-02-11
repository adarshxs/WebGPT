
# WebGPT

![webGPT](other/misc/header.png)

After six years of development, WebGPU is about to launch across most major web browsers. This is massive: web applications now have near-native access to the GPU, with the added capacity of compute shaders.

WebGPT is a vanilla JS and HTML implementation of a transformer model, intended as a proof-of-concept as well as educational resource. WebGPT has been tested to be working with models up to 500 M parameters, though could likely support far more with further testing/optimization.

At the moment, WebGPT averages ~130ms per token on GPT-2 124M running on a 2020 M1 Mac with Chrome Canary. This could be 500% faster, if not more, with proper optimization of the kernels, buffers, the WebGPU interface. WebGPU should also receive significant speed increases as it matures.

https://user-images.githubusercontent.com/30643741/233488471-0cd93d38-af27-4648-bbf6-46aa033e44a1.mp4

## Running WebGPT

Running WebGPT is remarkably simple, as it's just a set of HTML + JS files. Since WebGPU is still in the process of being released, you'll need to open with a compatible browser. WebGPU is currently available on Chrome v113 but the most straightforward way to ensure proper functionality is to install [Chrome Canary](https://www.google.com/chrome/canary/) and enable "Unsafe WebGPU" at `chrome://flags/#enable-unsafe-webgpu`.

If you get an error loading the models, specifically a CORS policy error, Here's what you can do: 

### quickly spin up a local web server to let your browser render local files

### Python 2
If you have Python installed...
Change directory into the folder using the command `cd /path/to/your/WebGPT/folder`

Start up a Python web server using the command `python -m SimpleHTTPServer`

This will start a web server to host your entire directory listing at `http://localhost:8000`

You can use a custom port `python -m SimpleHTTPServer 9000` giving you link: `http://localhost:9000`

### Python 3
Do the same steps, but use the following command instead `python3 -m http.server`

### VSCode
If you are using Visual Studio Code you can install the Live Server extension which provides a local web server enviroment.

### Node.js
Install http-server by typing `npm install -g http-server`

in your working directory, start your http server by issuing `http-server -c-1`

The model will be accessible from `http://localhost:8080 `

### Ruby
`ruby -run -e httpd . -p 8080`

### PHP
`php -S localhost:8000`


I've included two different models: a toy GPT-Shakespeare model (which is severly undertrained haha) and GPT-2 117M. See main.js for more information on how to run these models. If you want to import custom models, take a look at misc/conversion_scripts.

If you want to try out WebGPT, visit the demo website here [KMeans.org](https://www.kmeans.org). I'd generally reccomend cloning the repo and running locally, just because loading the weights remotely is significantly slower. Note: You'll need to use Git LFS to download the model files, after cloning the repository.

![file sizes](other/misc/files.png)

## Roadmap / Fixing Stupid Decisions

- [X] Embeddings / de-embeddings on GPU.
- [X] Initializing pipelines on every step is incredibly inefficient.
- [ ] Kernel shared memory!
- [ ] Convert into a package.
- [ ] Compute pass splitting for larger models *(maxStorageBufferBindingSize)*
- [ ] Key-value caching!!
- [ ] Write better comments + make Youtube explainer.

## Acknowledgements

When I started this project I had no idea how transformers worked or how to implement them (or GPUs or matmul kernels or WebGPU or tokenization for that matter), so Andrej Karpathy's series on neural networks and building GPT from scratch were invaluable: [Andrej's Youtube](https://www.youtube.com/@AndrejKarpathy). I've also used some code as well from the nanoGPT repository: [nanoGPT](https://github.com/karpathy/nanoGPT).

I copied from LatitudeGames' implementation of OpenAI's GPT-3 tokenizer in Javascript: [GPT-3-Encoder](https://github.com/latitudegames/GPT-3-Encoder).

## Note: I'm looking for work!

I'm currently in the process of switching into the AI field. I'm specifically looking for opportunites at larger research labs in a variety of jobs, with the goal of breaking into the space and finding an area in which to specialize. If you're interested, check out my personal website: [Personal Website](https://depue.design/)
