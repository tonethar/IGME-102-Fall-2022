# PE-17.5 - Adding a Pie Chart and Bar Graph

## Mission
1) Using PE-17 as a starting point, replace the map visualization with a pie chart (showing population) and a bar graph (showing the income properties you chose)

2) `readStates()` will still create an array of the 50+ states

3) After creating the array of states, `readStates()` will now call `updateViz()` with a single state
  - example: `updateViz(new State(states[1])); // pass over California`

4) `updateViz()` will now accept a `State` object as a parameter, and will then create a visualization using that state's data. Example:

```js
function updateViz(state){
  console.log(state);
  fill(255);
  textSize(36);
  let stateName = state.name;
  text("Facts about " + stateName,150,100);
  // now draw pie chart
  
  // now draw bar graph
```

5) Changing the `State` that is passed into `updateViz()` will chnage the visualization appropriately


- **Label 1**
![screenshot](_images/pe17-1.png)

- **Label 1**
![screenshot](_images/pe17-1.png)
