![header](https://capsule-render.vercel.app/api?type=waving&height=150&color=gradient&text=Ghaith%20Kelil&descAlign=82&fontAlignY=48&animation=fadeIn&section=header)



### 🌐 Connect with me

<p align="center">
  <a href="https://www.linkedin.com/in/ghaithkelil/" target="_blank">
    <img src="https://cdn2.iconfinder.com/data/icons/social-media-2285/512/1_Linkedin_unofficial_colored_svg-512.png" width="40" height="40"/>
  </a>
  <a href="https://www.instagram.com/ghaithkelil/" target="_blank">
    <img src="https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Instagram-512.png" width="40" height="40"/>
  </a>
</p>


name: Ghaith Kelil
located_in: Vantaa, Finland
current_job: IT Engineering Student at Metropolia  & Entrepreneur
education:
  [
    "ICT Engineering at Centria / Metropolia",
    "Web & Software Developer",
  ]

fields_of_interests:
  [
    "Web Development",
    "IoT & Embedded Systems",
    "Artificial Intelligence & Automation",
    "3D Modeling & Game Development",
    "Cloud & DevOps",
  ]
technical_background:
  [
    "Full Stack Web Development (Node.js, Express, React, SQL, Docker)",
    "IoT & Robotics Integration (MicroPython, MQTT, Firebase, Node-RED)",
    "Unity Game Development (C#)",
    "Linux System Administration",
    "E-commerce & Entrepreneurship (2k+ Etsy orders, 500+ reviews)",
    "Internship & Summer Jobs at Hertz Car Control",
  ]
  
2025 Goals: ["Complete thesis & internship", "Launch company web platform", "Build fitness/health app", "Explore AI & IoT projects"]
hobbies: ["Gym & Fitness", "Traveling", "Gaming", "Design", "Family Time"]


### 🚀 Some Tools I Have Used and Learned

<p align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/flutter/flutter-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/csharp/csharp-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/googlecloud/googlecloud-original-wordmark.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/react/react-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/cplusplus/cplusplus-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/azure/azure-original-wordmark.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/sqlite/sqlite-original-wordmark.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/typescript/typescript-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/unity/unity-original-wordmark.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/debian/debian-original-wordmark.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/dot-net/dot-net-original-wordmark.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/archlinux/archlinux-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/figma/figma-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg" width="40" height="40"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linux/linux-original.svg" width="40" height="40"/>
</p>

          

![footer](https://capsule-render.vercel.app/api?type=waving&height=100&color=gradient&section=footer)


name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
