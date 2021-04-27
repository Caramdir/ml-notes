# Sliding window detection

Train an image classifier with images of a fixed size and aspect ration. To detect in arbitrary images, take the trained aspect ratio and scan over the image, resizing each area to fit the trained images size. Do this at different scales.