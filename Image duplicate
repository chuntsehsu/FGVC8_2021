import imagehash
import numpy as np
import PIL
hash_functions = [
    imagehash.average_hash,
    imagehash.phash,
    imagehash.dhash,
    imagehash.whash]

image_ids = []
hashes = []

paths = tf.io.gfile.glob('./*.jpg')

for path in tqdm(paths, total=len(paths)):

    image = PIL.Image.open(path)

    hashes.append(np.array([x(image).hash for x in hash_functions]).reshape(-1,))
    image_ids.append(path.split('/')[-1])
    
hashes = np.array(hashes)
image_ids = np.array(image_ids)

duplicate_ids = []

for i in tqdm(range(len(hashes)), total=len(hashes)):
    similarity = (hashes[i] == hashes).mean(axis=1)
    duplicate_ids.append(list(image_ids[similarity > 0.85]))
    
duplicates = [frozenset([x] + y) for x, y in zip(image_ids, duplicate_ids)]
duplicates = set([x for x in duplicates if len(x) > 1])

for row in duplicates:
    
    figure, axes = plt.subplots(1, len(row), figsize=[5 * len(row), 5])

    for i, image_id in enumerate(row):
        image = plt.imread(os.path.join(train_dir, image_id))
        axes[i].imshow(image)

        axes[i].set_title(f'{image_id} - {df.loc[image_id, "labels"]}')
        axes[i].axis('off')
