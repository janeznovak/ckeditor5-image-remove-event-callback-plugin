# demo-remove-image

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Steps for reproducing the problem

1. Go to http://localhost:8080/.
2. Open the developers console(right click -> inspect or F12)
3. Click on the source button.
4. Put this in: ```<img src="https://www.planetware.com/wpimages/2020/02/france-in-pictures-beautiful-places-to-photograph-eiffel-tower.jpg">```.
5. Click on the source one more time.
6. Now the image is visible.
7. Click on the image and press delete.
8. Check the developers console where it logged out: 

9. You can see that the name of the removed object, which is inlineImage.