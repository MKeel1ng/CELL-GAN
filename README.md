## CELL-GAN
This is a project to create plausible cell fluorescence images using a generative adversarial network (GAN).

## DATA:
cell images of any size can be used, the code prepares data by flipping and resizing to the desired size. The whole data set is saved as a numpy array to accelerate training

## TRAINING:

recommended settings:

activation='LeakyReLU' #The final activation in the generator will be a LeakyReLU, with the data scaled between 0 and 1. This seems to work better in achieving the uniform dark background. set activation='tanh' for a traditional approach

epochs = 500 #depends on dataset size

BATCH_SIZE = 32 #depends on image size, maximise as much as memory allows
noise_dim = 128 #increase in case of mode collapse
wd=0.001 #sets weight decay, play around
resblocks=True #adds skip connections
self_attention=True #adds a self attention layer. location can be controlled in **get_generator_model** and **get_discriminator_model** with the **self_attention_layer** parameter
base_filters=64 #depends on memory


adapted from: **https://keras.io/examples/generative/wgan_gp/**

