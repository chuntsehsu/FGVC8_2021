import plotly.express as px
import cv2
import numpy as np
def new_cont(img1,img2):

  img1 = cv2.resize(img1, target_size)
  img2 = cv2.resize(img2, target_size)


  h1, w1 ,c1= img1.shape
  h2, w2 ,c1= img2.shape

  img11 = img1[:h1,:w1//2]
  img21 = img2[:h1,w1//2:]
  img_mix1 = cv2.hconcat([img11, img21])

  img21 = img2[:h1,:w1//2]
  img22 = img1[:h1,w1//2:]
  img_mix2 = cv2.hconcat([img21, img22])

  fig, ax = plt.subplots(nrows=1, ncols=4, figsize=(30, 20))
  ax[0].imshow(img1, cmap='gray')
  ax[0].set_title('img1', fontsize=24)
  ax[1].imshow(img2, cmap='gray')
  ax[1].set_title('img2', fontsize=24)
  ax[2].imshow(img_mix1, cmap='gray')
  ax[2].set_title('img_mix1', fontsize=24)
  ax[3].imshow(img_mix2, cmap='gray')
  ax[3].set_title('img_mix2', fontsize=24)

  plt.show()
