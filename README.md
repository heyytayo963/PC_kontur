# pc_kontur

## Menggunakan *Skeletonize(image)*

#### Input
```
image = invert(data.horse())
```

```
# Perform skeletonization
skeleton = skeletonize(image)
```

```
# Display Result
fig, axes = plt.subplots(nrows=1, ncols=2, figsize = (8, 4), sharex=True, sharey=True)

ax = axes.ravel()

ax[0].imshow(image, cmap=plt.cm.gray)
ax[0].axis('off')
ax[0].set_title('Original', fontsize=20)

ax[1].imshow(skeleton, cmap=plt.cm.gray)
ax[1].axis('off')
ax[1].set_title('Skeleton', fontsize=20)

fig.tight_layout()
st.pyplot(fig)
```
#### Output : 
![ra](https://github.com/heyytayo963/PC_kontur/assets/115687740/ea18a547-5aea-4513-b46c-8bce12b7cf38)

## Menggunakan *Activate Contour*

## Input : 
```
img2 = data.astronaut()
img3 = rgb2gray(img2)
```

```
# Data fro circular boundary
s = np.linspace(0, 2*np.pi, 400)
x = 100 + 100*np.cos(s)
y = 220 + 100*np.sin(s)
init = np.array([x, y]).T
```

```
# Formation of the active contour
cntr = active_contour(gaussian(img2, sigma=3, preserve_range=False),
    init,
    alpha=0.015,
    beta=10,
    gamma=0.001,
)
```

```
fig, ax = plt.subplots(1, 2, figsize=(7, 7))
```

```
ax[0].imshow(img2, cmap=plt.cm.gray)
ax[0].set_title('Original Image')
```

```
# Circular boundary
ax[1].imshow(img2, cmap=plt.cm.gray)
ax[1].plot(init[:, 1], init[:, 0], '--r', lw=3)
ax[1].plot(cntr[:, 1], cntr[:, 0], '-b', lw=3)
ax[1].set_xticks([]), 
ax[1].set_yticks([])
ax[1].axis([0, img2.shape[1], img2.shape[0], 0])
ax[1].set_title('Active Contour Image')
```

```
fig.tight_layout()
st.pyplot(fig)
```

#### Output : 
![ra1](https://github.com/heyytayo963/PC_kontur/assets/115687740/3cf65855-c224-40a3-a79d-9412da5339fe)
