# Anarchist Overlay

## Config
```js
//Overlay config
export type OverlayConfig = {
  positionX?: string; // 'start', 'center' or 'end'
  positionY?: string; // 'start', 'center' or 'end'
  fadeOnClose?: boolean; // should overlay fade out after closeTime
  closeTime?: number; // how long overlay should stay open, in seconds
  closeAllWindows?: boolean; // should all windows (character sheets etc.) be closed before overlay initialization
  aboveUi?: boolean; // should it render above or under UI (above blocks interactivity until overlay closes
}
//Text config
export type TextCrawlConfig = {
  offsetX?: string; // for example '15px'
  offsetY?: string; // for example '15px'
  typingTime?: number, // how long (in seconds) does the typing animation take per one line
  delay?: number, // how long (in seconds) does the typing animation pause before next line is typed
  blackBars?: boolean, // should black bars on top and bottom be rendered
  lines: { text: string, fontSize?: string }[] // list of lines to be rendered
};
```


Example usage:

```js

const overlayConfig = {
  positionX: 'start',
  positionY: 'center'
}

const textConfig = {
  offsetX: '20px',
  offsetY: '0',
  typingTime: 2,
  delay: 1,
  blackBars: true,
  lines: [{
      text: 'MISSION 1: BUG HUNT',
      fontSize: '52px',
    },
    {
      text: 'COMBAT: TRAPDOOR SPIDER',
      fontSize: '38px',
    },
    {
      text: 'OBJECTIVE: SEARCH AND DESTROY',
      fontSize: '34px'
    },
    {
      text: 'EARLY SPRING, 5014U | HERCYNIA',
      fontSize: '20px'
    },
    {
      text: 'FOREST NEAR EVERGREEN | WEATHER: EXTREME HUMIDITY',
      fontSize: '20px'
    },
  ]
}


const anarchistOverlay = game.modules.get('anarchist-overlay');
textHtml = await anarchistOverlay.createTextCrawlHtml(textConfig);


anarchistOverlay.createOverlay(overlayConfig, textHtml);

```
Effect:

![Animation](https://user-images.githubusercontent.com/10486394/233835406-5a02eaf6-3374-491b-97ba-813512fab075.gif)
