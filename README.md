
## STARTING WITH DOCKER
First we need to download the docker image and import it locally. After the image has been imported, you can see a list of the images you have currently installed and run a given docker image by executing the following commands. For the **retrieval chatbot**:

```bash
docker load -i retrieval_docker.tar
docker run -it -e PASSWORD=password -p 8888:8888 retrieval-chatbot:0.12.1
```

For the **generative chatbot**:

```bash
docker load -i generative_docker.tar
docker run -it -e PASSWORD=password -p 8888:8888 generative-chatbot:1.1.0
```

## NOTEBOOKS

Now we can go to http://localhost:8888/ (we have set "password" as the password to access the notebooks). There you will see all the files and directories you are going to use with this chatbot, including the notebook. Follow the instructions on the videos as walkthrough for the notebooks.

## MAKING AND SAVING CHANGES
If we update the notebooks with our own code or we have new checkpoints saved and we want the docker image to save them for the next time we execute it, we need to commit the changes. To do that, you have to:
1. See the id of the container you are running with 

```bash
docker image list
```

2. Take the id of the original image you want to update. In this case it's going to be either **retrieval-chatbot:0.12.1** or **generative-chatbot:1.1.0**

3. Commit the changes with

```bash
docker commit your_container_id your_image_id
```

4. Done! Next time you run an image it will have your changes updated

If you want to run the **retrieval chatbot** checkpoint in a different environment out of Docker, you have to change the path written in the checkpoint. If you go to */runs/the_checkpoint_id/checkpoint* file, you will see the absolute path of the location of the checkpoint. Please, change it to your own path or it will raise and error while loading the model.

## REFERENCES

Original code and dataset can be found in:
- Retrieval Chatbot: https://github.com/dennybritz/chatbot-retrieval
- Generative Chatbot:  https://github.com/Conchylicultor/DeepQA
- Ubuntu Corpus: https://drive.google.com/file/d/0B_bZck-ksdkpVEtVc1R6Y01HMWM/view




