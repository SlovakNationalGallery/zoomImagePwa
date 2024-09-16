# zoomImagePwa

A simple Progressive Web App (PWA) built using Vite and Vue.js, featuring pinch-to-zoom functionality for image. The app is based on `@vite-pwa/pwa` and uses the `zoompinch` library for handling zoom gestures.

## Features

- **Pinch-to-Zoom**: Users can pinch to zoom on an image using touch gestures, perfect for mobile devices.
- **Vite-Powered PWA**: Built using Vite for lightning-fast development and instant loading as a Progressive Web App.
- **Responsive Design**: The app runs in fullscreen mode on iPads and other devices, providing a smooth, touch-friendly experience.

## Installation

1. Clone the repository:

   ```bash
   git clone git@github.com:SlovakNationalGallery/zoomImagePwa.git
   cd zoomImagePwa
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Place your high-resolution image in the `src/assets/` folder and update the image path in `ImageZoom.vue`.

## Development

To run the app in development mode:

```bash
npm run dev
```

This will start the Vite development server for testing.

## Build

To build the app for production:

```bash
npm run build
```

This will create the optimized output in the `dist` folder, ready for deployment.

## Usage

Once deployed, you can install the app on a mobile device or desktop by navigating to the site and adding it to your home screen via the browser’s "Add to Home Screen" feature. It will run as a PWA in fullscreen mode.

## ZoomPinch Library

This project integrates [ZoomPinch](https://github.com/MauriceConrad/zoompinch) to handle pinch-to-zoom gestures on touch devices. 

## License

This project is licensed under the MIT License. Feel free to reuse and modify the code as needed.
