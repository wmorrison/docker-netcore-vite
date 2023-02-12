# Dockerize-React

### Using Vite


##### Allow application changes (HMR) to sync to the folder inside of our docker app
Added `usePolling: true` to `vite.config` in order to allow for polling changes to the docker bind:mount volume.
```js
export default defineConfig({
  plugins: [react()],
  server: {
    watch: {
      usePolling: true
    }
  }
});
```

in the command to create our docker container we add the following to bind our src directory to the docker volume:
```docker
'-v %cd%\\src:/app/src'

docker run -v %cd%\\src:/app/src -d -p 5173:5173 --name react-app dockerize-react-image
```

