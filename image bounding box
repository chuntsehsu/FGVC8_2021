import matplotlib.pyplot as plt
def edge_and_cut(img):
    copy_img = img.copy()
    img1 = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
    edges = cv2.Canny(img1, 155, 165)
    edge_box = []
    for i in range(edges.shape[0]):
        for j in range(edges.shape[1]):
            if edges[i][j] != 0:
                edge_box.append((i, j))
    
    row_min = edge_box[np.argsort([box[0] for box in edge_box])[0]][0]
    row_max = edge_box[np.argsort([box[0] for box in edge_box])[-1]][0]
    col_min = edge_box[np.argsort([box[1] for box in edge_box])[0]][1]
    col_max = edge_box[np.argsort([box[1] for box in edge_box])[-1]][1]
    new_img = img[row_min:row_max, col_min:col_max]
    
    copy_img[row_min-10:row_min+10, col_min:col_max] = [255, 0, 0]
    copy_img[row_max-10:row_max+10, col_min:col_max] = [255, 0, 0]
    copy_img[row_min:row_max, col_min-10:col_min+10] = [255, 0, 0]
    copy_img[row_min:row_max, col_max-10:col_max+10] = [255, 0, 0]
    
    fig, ax = plt.subplots(nrows=1, ncols=5, figsize=(30, 20))
    ax[0].imshow(img, cmap='gray')
    ax[0].set_title('Original Image', fontsize=24)
    ax[1].imshow(img1, cmap='gray')
    ax[1].set_title('gray Image', fontsize=24)
    ax[2].imshow(edges, cmap='gray')
    ax[2].set_title('Canny Edges', fontsize=24)
    ax[3].imshow(copy_img, cmap='gray')
    ax[3].set_title('Bounding Box', fontsize=24)
    ax[4].imshow(new_img, cmap='gray')
    ax[4].set_title('New Image', fontsize=24)
    plt.show()
