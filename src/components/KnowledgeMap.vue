<template>
    <div id="app">
      <h1 class="title">Knowledge Map</h1>
      <div id="cy"></div>
    </div>
  </template>
  
  <script>
  import cytoscape from "cytoscape";
  
  export default {
    name: "KnowledgeMap",
    mounted() {
      const cy = cytoscape({
        container: document.getElementById("cy"), // container to render in
  
        elements: [
          // Main Nodes
          { data: { id: "0", label: "0. Foundations" } },
          { data: { id: "1", label: "1. Basic ROS2" } },
          { data: { id: "2", label: "2. ROS Basics" } },
          { data: { id: "3", label: "3. Intermediate ROS2" } },
          { data: { id: "4", label: "4. Robotics Theory" } },
          { data: { id: "5", label: "5. Navigation ROS2" } },
          { data: { id: "7", label: "7. Manipulation" } },
          { data: { id: "8", label: "8. Robot Creation" } },
          { data: { id: "9", label: "9. Artificial Intelligence" } },
          { data: { id: "10", label: "10. ROS Debugging" } },
          { data: { id: "11", label: "11. Course of Product" } },
          { data: { id: "12", label: "12. Webtools for Robotics" } },
          { data: { id: "13", label: "13. Simulation" } },
          { data: { id: "14", label: "14. Enterprise" } },
  
          // Sub-nodes
          { data: { id: "linux", label: "Linux for Robotics" } },
          { data: { id: "link", label: "Create a Link" } },
          { data: { id: "cpp", label: "C++ for Robotics" } },
          { data: { id: "python", label: "Python 3 for Robotics" } },
          { data: { id: "gazebo", label: "Gazebo Sim with ROS2" } },
          { data: { id: "tf", label: "TF in ROS2" } },
          { data: { id: "urdf", label: "URDF Robot Modelling ROS2" } },
          { data: { id: "ros2_cpp", label: "ROS2 Basics in 5 Days (C++)" } },
          { data: { id: "ros2_python", label: "ROS2 Basics in 5 Days (Python)" } },
          { data: { id: "ros2_rust", label: "ROS2 Basics in 3 Days (Rust)" } },
          { data: { id: "nav_advanced", label: "Nav Advanced" } },
          { data: { id: "nav2", label: "Nav2 Basics" } },
          { data: { id: "rtab", label: "RTAB" } },
          { data: { id: "control", label: "ROS2 Control" } },
          { data: { id: "inter_cpp", label: "Intermediate ROS2 (C++)" } },
          { data: { id: "inter_python", label: "Intermediate ROS2 (Python)" } },
          { data: { id: "modern_cpp", label: "Advanced Modern C++ for Robotics" } },
          { data: { id: "behavior", label: "Behavior Trees for ROS2" } },
          { data: { id: "migration", label: "ROS1-ROS2 Migration" } },
  
          // Edges
          { data: { source: "0", target: "linux" } },
          { data: { source: "0", target: "link" } },
          { data: { source: "0", target: "cpp" } },
          { data: { source: "0", target: "python" } },
          { data: { source: "0", target: "1" } },
          { data: { source: "0", target: "2" } },
          { data: { source: "2", target: "gazebo" } },
          { data: { source: "1", target: "tf" } },
          { data: { source: "1", target: "urdf" } },
          { data: { source: "1", target: "ros2_cpp" } },
          { data: { source: "1", target: "ros2_python" } },
          { data: { source: "1", target: "ros2_rust" } },
          { data: { source: "1", target: "5" } },
          { data: { source: "5", target: "nav_advanced" } },
          { data: { source: "5", target: "nav2" } },
          { data: { source: "5", target: "rtab" } },
          { data: { source: "1", target: "3" } },
          { data: { source: "3", target: "control" } },
          { data: { source: "3", target: "inter_cpp" } },
          { data: { source: "3", target: "inter_python" } },
          { data: { source: "3", target: "modern_cpp" } },
          { data: { source: "3", target: "behavior" } },
          { data: { source: "3", target: "migration" } },
        ],
  
        style: [
          {
            selector: "node",
            style: {
              "background-color": "#4A90E2",
              "text-valign": "center",
              "text-halign": "center",
              label: "data(label)",
              color: "#000", // Set text color to black for all nodes
              "font-size": "12px",
              "font-weight": "bold",
              width: "50px", // Fixed size for a consistent circular node size
              height: "50px", // Fixed size for a consistent circular node size
              "border-width": 2,
              "border-color": "#fff", // Light border to make nodes stand out
              shape: "ellipse", // Ensures that the node is always circular
            },
          },
          {
            selector: "node[id = '0'], node[id = '1'], node[id = '2'], node[id = '3'], node[id = '4'], node[id = '5'], node[id = '7'], node[id = '8'], node[id = '9'], node[id = '10'], node[id = '11'], node[id = '12'], node[id = '13'], node[id = '14']",
            style: {
              "background-color": "#FFCC00", // Set a different background color for main nodes
            },
          },
          {
            selector: "edge",
            style: {
              "width": 2,
              "line-color": "#aaa",
              "target-arrow-color": "#aaa",
              "target-arrow-shape": "triangle",
              "curve-style": "bezier", // Smooth curve for edges
            },
          },
        ],
  
        layout: {
          name: "circle", // Circular layout for nodes
          padding: 50, // Adds space for nodes in the circle layout
        },
      });
    },
  };
  </script>
  
  <style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body {
    margin: 0;
    font-family: Arial, sans-serif;
  }
  
  #app {
    height: 100vh;
    display: flex;
    flex-direction: column;
  }
  
  .title {
    margin: 0;
    padding: 10px;
    background-color: #4A90E2;
    color: white;
    text-align: center;
    font-size: 24px;
  }
  
  #cy {
    flex-grow: 1;
    border: 1px solid #ddd;
    background-color: #f9f9f9; /* Slightly lighter background for a clean look */
  }
  </style>
  
  