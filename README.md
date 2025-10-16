<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Workout Split and Diet (by Thushar)</title>
  <style>
    body {
      background: #000;
      color: #fff;
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      min-height: 100vh;
      position: relative;
    }
    .dumbbell-logo {
      position: absolute;
      top: 18px;
      right: 28px;
      font-size: 2.3rem;
      user-select: none;
      z-index: 100;
    }
    .main-container {
      max-width: 900px;
      margin: 80px auto 0 auto;
      padding: 2rem;
      background: #222;
      border-radius: 12px;
      box-shadow: 0 4px 24px rgba(0,0,0,0.3);
      min-height: 600px;
    }
    h1 {
      text-align: center;
      margin-top: 0;
      font-size: 2.2em;
    }
    .muscle-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 2rem;
      margin: 2rem 0;
    }
    .muscle-card {
      background: #333;
      border-radius: 16px;
      box-shadow: 0 2px 12px rgba(0,0,0,.3);
      padding: 1.5rem;
      width: 170px;
      text-align: center;
      cursor: pointer;
      transition: transform 0.12s;
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .muscle-card:hover {
      transform: translateY(-6px) scale(1.03);
      box-shadow: 0 6px 24px #00ffe7a0;
      background: #444;
    }
    .muscle-icon {
      font-size: 2.4em;
      margin-bottom: 0.3em;
      user-select: none;
    }
    .muscle-label {
      font-size: 1.15em;
      font-weight: bold;
      margin-bottom: 0.2em;
      letter-spacing: 0.5px;
    }
    .exercise-list, .diet-list {
      margin: 2rem auto 0 auto;
      max-width: 600px;
      background: #222;
      border-radius: 12px;
      box-shadow: 0 2px 12px rgba(0,0,0,0.3);
      padding: 1.5rem 2rem;
      animation: fadeIn 0.3s;
    }
    .exercise-title, .diet-title {
      font-size: 1.4em;
      margin-top: 0;
      margin-bottom: 0.7em;
      text-align: center;
    }
    ul.exercise-ul {
      list-style: none;
      padding-left: 0;
      margin-top: 0.5em;
      margin-bottom: 0;
    }
    ul.exercise-ul li {
      margin-bottom: 0.6em;
      font-size: 1.12em;
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #333;
      border-radius: 8px;
      padding: 0.6em 0.7em;
      box-shadow: 0 1px 6px rgba(0,255,231,0.04);
    }
    .howto-link {
      margin-left: 1em;
      font-size: 0.98em;
      color: #00ffe7;
      text-decoration: underline;
      background: none;
      border: none;
      cursor: pointer;
      font-family: inherit;
      padding: 0.16em 0.4em;
    }
    .back-link {
      margin-top: 1.5em;
      color: #00ffe7;
      text-decoration: underline;
      cursor: pointer;
      font-size: 1.1em;
      background: none;
      border: none;
      padding: 0;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
    .hidden {
      display: none;
    }
    .howto-slide {
      background: #333;
      color: #fff;
      padding: 1em 1.5em;
      border-radius: 8px;
      margin: 1em auto 0 auto;
      width: 90%;
      animation: fadeIn 0.3s;
      box-shadow: 0 2px 12px rgba(0,0,0,0.23);
      max-width: 560px;
    }
    @keyframes fadeIn {
      from { opacity: 0;}
      to { opacity: 1;}
    }
    .howto-title {
      font-size: 1.15em;
      margin-top: 0;
    }
    .howto-close {
      float: right;
      font-size: 1em;
      color: #00ffe7;
      background: none;
      border: none;
      cursor: pointer;
      text-decoration: underline;
      margin-top: -0.5em;
      margin-right: -1em;
    }
    .bmi-inputs {
      display: flex;
      gap: 1em;
      margin-bottom: 1em;
      align-items: center;
      flex-wrap: wrap;
    }
    .bmi-inputs label {
      font-size: 1em;
      color: #00ffe7;
    }
    .bmi-inputs input {
      padding: 0.4em 0.7em;
      border-radius: 6px;
      border: none;
      font-size: 1em;
      background: #333;
      color: #fff;
      width: 90px;
      margin-left: 0.3em;
    }
    .bmi-btn {
      padding: 0.5em 1.2em;
      border-radius: 6px;
      border: none;
      background: #00ffe7;
      color: #000;
      font-size: 1em;
      cursor: pointer;
      font-weight: bold;
      margin-left: 1em;
      margin-top: 0.5em;
    }
    .bmi-btn:hover {
      background: #00c7b1;
    }
    .bmi-result {
      margin: 1em 0 0 0;
      font-size: 1.1em;
      color: #fff;
      background: #333;
      border-radius: 8px;
      padding: 1em;
    }
    .diet-food-list {
      margin-top: 1em;
      background: #222;
      border-radius: 8px;
      padding: 1em 1.5em;
      color: #fff;
      box-shadow: 0 1px 8px #00ffe71a;
    }
    .diet-food-list h4 {
      color: #00ffe7;
      margin-top: 0.2em;
      margin-bottom: 0.7em;
    }
    .diet-food-list ul {
      margin-bottom: 0;
    }
  </style>
</head>
<body>
  <div class="dumbbell-logo" title="Dumbbell Logo">🏋️‍♂️</div>
  <div class="main-container">
    <h1>Workout Split and Diet <small>(by Thushar)</small></h1>
    <!-- Muscle group cards -->
    <div class="muscle-grid" id="muscleGrid">
      <div class="muscle-card" onclick="showExercises('biceps')">
        <span class="muscle-icon">💪</span>
        <span class="muscle-label">Biceps</span>
      </div>
      <div class="muscle-card" onclick="showExercises('triceps')">
        <span class="muscle-icon">🦾</span>
        <span class="muscle-label">Triceps</span>
      </div>
      <div class="muscle-card" onclick="showExercises('shoulders')">
        <span class="muscle-icon">🏋️‍♂️</span>
        <span class="muscle-label">Shoulders</span>
      </div>
      <div class="muscle-card" onclick="showExercises('chest')">
        <span class="muscle-icon">🏆</span>
        <span class="muscle-label">Chest</span>
      </div>
      <div class="muscle-card" onclick="showExercises('back')">
        <span class="muscle-icon">🛡️</span>
        <span class="muscle-label">Back</span>
      </div>
      <div class="muscle-card" onclick="showExercises('legs')">
        <span class="muscle-icon">🦵</span>
        <span class="muscle-label">Legs</span>
      </div>
      <div class="muscle-card" onclick="showDiet()">
        <span class="muscle-icon">🍽️</span>
        <span class="muscle-label">Diet</span>
      </div>
    </div>
    <!-- Exercise list slide -->
    <div id="exerciseSection" class="exercise-list hidden"></div>
    <!-- Diet slide -->
    <div id="dietSection" class="diet-list hidden">
      <h2 class="diet-title">Diet & BMI Recommendations</h2>
      <p>
        <strong>Body Mass Index (BMI)</strong> is a value derived from the height and weight of a person. It helps classify individuals as underweight, normal weight, overweight, or obese.<br>
        <br>
        <em>BMI = Weight (kg) / [Height (m)]<sup>2</sup></em>
      </p>
      <form autocomplete="off">
        <div class="bmi-inputs">
          <label>Height (cm): <input type="number" min="100" max="250" required id="heightInput" placeholder="e.g. 170"></label>
          <label>Weight (kg): <input type="number" min="30" max="200" required id="weightInput" placeholder="e.g. 65"></label>
          <button class="bmi-btn" type="button" onclick="calcBMI()">Calculate BMI</button>
        </div>
      </form>
      <div id="bmiResult" class="bmi-result"></div>
      <div id="dietFoodList" class="diet-food-list"></div>
      <button class="back-link" onclick="showMuscleGrid()">← Back to muscle groups</button>
    </div>
    <!-- How to slide -->
    <div id="howtoSection"></div>
  </div>
  <script>
    // Muscle group data (unchanged)
    const muscleData = {
      biceps: {
        title: "Biceps",
        info: "Biceps are smaller muscles and can be trained along with bigger muscles like back. As back and biceps are pulling exercises, the muscle tension is more and they can be combined with back exercises.",
        exercises: [
          { name: "Bicep alternate curls", key: "bicep-alternate-curls" },
          { name: "Spider curls", key: "spider-curls" },
          { name: "Hammer curls", key: "hammer-curls" },
          { name: "Hammer with rope", key: "hammer-with-rope" },
          { name: "Preacher curls", key: "preacher-curls" },
          { name: "Behind the hip cable curls", key: "behind-hip-cable-curls" },
          { name: "Concentration curls", key: "concentration-curls" },
          { name: "Cable curls", key: "cable-curls" },
          { name: "EZ-bar curls", key: "ez-bar-curls" },
          { name: "Incline dumbbell curls", key: "incline-dumbbell-curls" },
          { name: "Chin-ups (focus on biceps)", key: "chin-ups-biceps" }
        ]
      },
      triceps: {
        title: "Triceps",
        info: "Triceps are the muscle group at the back of your upper arm. They are trained with pushing exercises and are important for overall arm size and strength.",
        exercises: [
          { name: "Tricep pushdowns", key: "tricep-pushdowns" },
          { name: "Overhead tricep extension", key: "overhead-tricep-extension" },
          { name: "Skullcrushers", key: "skullcrushers" },
          { name: "Close-grip bench press", key: "close-grip-bench-press" },
          { name: "Bench dips", key: "bench-dips" }
        ]
      },
      shoulders: {
        title: "Shoulders",
        info: "Shoulders consist of three heads: front (anterior), side (lateral), and rear (posterior). Shoulder workouts improve strength, stability, and aesthetics.",
        exercises: [
          { name: "Overhead press", key: "overhead-press" },
          { name: "Lateral raises", key: "lateral-raises" },
          { name: "Front raises", key: "front-raises" },
          { name: "Rear delt fly", key: "rear-delt-fly" },
          { name: "Arnold press", key: "arnold-press" }
        ]
      },
      chest: {
        title: "Chest",
        info: "Chest muscles are worked with pushing exercises and help with upper body strength and aesthetics.",
        exercises: [
          { name: "Barbell bench press", key: "barbell-bench-press" },
          { name: "Dumbbell bench press", key: "dumbbell-bench-press" },
          { name: "Incline bench press", key: "incline-bench-press" },
          { name: "Chest fly", key: "chest-fly" },
          { name: "Push-ups", key: "push-ups" }
        ]
      },
      back: {
        title: "Back",
        info: "Back is one of the largest muscle groups and is responsible for pulling movements. Training back helps improve posture, strength, and aesthetics.",
        exercises: [
          { name: "Pull-ups", key: "pull-ups" },
          { name: "Lat pulldown", key: "lat-pulldown" },
          { name: "Barbell rows", key: "barbell-rows" },
          { name: "Seated cable rows", key: "seated-cable-rows" },
          { name: "T-bar rows", key: "t-bar-rows" },
          { name: "Single-arm dumbbell rows", key: "single-arm-dumbbell-rows" },
          { name: "Straight-arm pulldown", key: "straight-arm-pulldown" }
        ]
      },
      legs: {
        title: "Legs",
        info: "Leg workouts build overall strength and athleticism. They target quadriceps, hamstrings, calves, and glutes.",
        exercises: [
          { name: "Barbell squats", key: "barbell-squats" },
          { name: "Leg press", key: "leg-press" },
          { name: "Lunges", key: "lunges" },
          { name: "Leg extension", key: "leg-extension" },
          { name: "Leg curl", key: "leg-curl" },
          { name: "Standing calf raises", key: "standing-calf-raises" }
        ]
      }
    };

    // Diet recommendation data (unchanged)
    const dietData = {
      underweight: {
        title: "Underweight (BMI < 18.5)",
        foods: [
          "Whole milk, paneer, cheese",
          "Rice, potatoes, whole wheat rotis",
          "Banana, mango, dry fruits",
          "Eggs, chicken, fish",
          "Nuts, peanut butter",
          "Ghee, healthy oils (olive, mustard)"
        ],
        tips: "Eat calorie-dense, nutritious foods. Aim for 5-6 small meals a day. Include strength training to build muscle."
      },
      normal: {
        title: "Normal weight (BMI 18.5 - 24.9)",
        foods: [
          "Brown rice, whole grains",
          "Seasonal vegetables, salads",
          "Lean proteins: dal, eggs, chicken, fish",
          "Fruits: apple, orange, papaya, berries",
          "Low-fat dairy: curd, milk",
          "Nuts and seeds"
        ],
        tips: "Consume a balanced diet with carbs, proteins, fats, vitamins, and minerals. Focus on variety and moderation."
      },
      overweight: {
        title: "Overweight (BMI 25 - 29.9)",
        foods: [
          "Whole grains in small portions",
          "Leafy greens, fiber-rich veggies",
          "Lean proteins: grilled chicken, fish, tofu",
          "Fruits (avoid high-sugar): apple, orange, berries",
          "Low-fat dairy",
          "Nuts (in moderation)"
        ],
        tips: "Limit processed foods, sugar, and fried items. Focus on high-fiber foods and regular exercise."
      },
      obese: {
        title: "Obese (BMI 30+)",
        foods: [
          "Leafy greens, cruciferous veggies",
          "Low-calorie fruits: watermelon, berries",
          "Skinless chicken, fish, dal",
          "Whole grains in small portions",
          "Low-fat dairy",
          "Legumes, beans"
        ],
        tips: "Adopt a calorie deficit diet with medical guidance. Avoid sugar, fried foods, and excess carbs. Increase physical activity."
      }
    };

    // All exercise instructions (for all muscle groups)
    const howtoContent = {
      // Biceps
      'bicep-alternate-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Bicep Alternate Curls - How to</h3>
          <ol>
            <li>Stand straight with dumbbells in each hand, palms facing forward.</li>
            <li>Keep elbows close to your torso, upper arms stationary.</li>
            <li>Curl right dumbbell, contracting your biceps.</li>
            <li>Pause at the top, lower slowly, repeat left side.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t swing your body; use controlled motion.</li>
            <li>Keep your back straight.</li>
            <li>Squeeze the biceps at the top.</li>
          </ul>
        </div>`,
      'spider-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Spider Curls - How to</h3>
          <ol>
            <li>Lie face down on an incline bench, arms hanging straight down.</li>
            <li>Curl dumbbells upward, squeezing biceps.</li>
            <li>Pause at the top, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep elbows pointed straight down.</li>
            <li>Use full range of motion.</li>
          </ul>
        </div>`,
      'hammer-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Hammer Curls - How to</h3>
          <ol>
            <li>Stand with dumbbells at your sides, palms facing your torso.</li>
            <li>Curl both weights upward, keeping wrists neutral.</li>
            <li>Pause, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t rotate wrists.</li>
            <li>Keep elbows close to torso.</li>
          </ul>
        </div>`,
      'hammer-with-rope': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Hammer Curls with Rope - How to</h3>
          <ol>
            <li>Attach rope to cable machine, grip both ends, thumbs up.</li>
            <li>Curl rope upward, keeping elbows fixed at sides.</li>
            <li>Pause, return to start.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Squeeze at the top for maximal contraction.</li>
          </ul>
        </div>`,
      'preacher-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Preacher Curls - How to</h3>
          <ol>
            <li>Sit at preacher bench, arms over pad holding barbell/dumbbells.</li>
            <li>Curl weight upward, keeping upper arm on pad.</li>
            <li>Pause, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t lift elbows off pad.</li>
            <li>Use controlled motion.</li>
          </ul>
        </div>`,
      'behind-hip-cable-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Behind the Hip Cable Curls - How to</h3>
          <ol>
            <li>Attach single handle to low cable, stand sideways.</li>
            <li>Grab handle with outside hand, arm behind hip.</li>
            <li>Curl handle forward, keeping elbow behind body.</li>
            <li>Pause, return to start.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep upper arm stationary.</li>
          </ul>
        </div>`,
      'concentration-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Concentration Curls - How to</h3>
          <ol>
            <li>Sit on bench, hold dumbbell in one hand, elbow against inner thigh.</li>
            <li>Curl dumbbell upward, pause, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t swing or use momentum.</li>
            <li>Squeeze biceps at top.</li>
          </ul>
        </div>`,
      'cable-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Cable Curls - How to</h3>
          <ol>
            <li>Attach straight bar to low cable.</li>
            <li>Stand facing cable, grip bar with both hands.</li>
            <li>Curl bar upward, pause, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep elbows close to sides.</li>
          </ul>
        </div>`,
      'ez-bar-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">EZ-Bar Curls - How to</h3>
          <ol>
            <li>Stand holding EZ bar, shoulder-width grip.</li>
            <li>Keep elbows at sides, curl bar upward.</li>
            <li>Pause, lower under control.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Squeeze at the top.</li>
          </ul>
        </div>`,
      'incline-dumbbell-curls': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Incline Dumbbell Curls - How to</h3>
          <ol>
            <li>Sit on incline bench, arms hanging holding dumbbells.</li>
            <li>Curl weights upward, keeping elbows pointed down.</li>
            <li>Pause, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t swing weights.</li>
          </ul>
        </div>`,
      'chin-ups-biceps': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Chin-Ups (Focus on Biceps) - How to</h3>
          <ol>
            <li>Grab chin-up bar with underhand grip, hands shoulder-width.</li>
            <li>Hang with arms fully extended.</li>
            <li>Pull up until chin is above bar, lower under control.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Focus on biceps, not just back.</li>
            <li>Don’t swing legs.</li>
          </ul>
        </div>`,
      // Triceps
      'tricep-pushdowns': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Tricep Pushdowns - How to</h3>
          <ol>
            <li>Stand facing cable machine, grip bar overhand.</li>
            <li>Keep elbows close to torso, push bar down until arms are straight.</li>
            <li>Slowly return to start.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Squeeze triceps at bottom.</li>
          </ul>
        </div>`,
      'overhead-tricep-extension': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Overhead Tricep Extension - How to</h3>
          <ol>
            <li>Hold dumbbell or bar overhead, arms extended.</li>
            <li>Bend elbows, lower weight behind head.</li>
            <li>Extend arms to start position.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep upper arms stationary.</li>
          </ul>
        </div>`,
      'skullcrushers': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Skullcrushers - How to</h3>
          <ol>
            <li>Lie on bench, hold barbell arms extended.</li>
            <li>Bend elbows, lower bar toward forehead.</li>
            <li>Extend arms to lift bar up.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Use controlled motion.</li>
          </ul>
        </div>`,
      'close-grip-bench-press': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Close-Grip Bench Press - How to</h3>
          <ol>
            <li>Lie on bench, grip barbell hands closer than shoulder width.</li>
            <li>Lower bar to chest, press up.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep elbows close to body.</li>
          </ul>
        </div>`,
      'bench-dips': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Bench Dips - How to</h3>
          <ol>
            <li>Place hands on bench behind you, feet out in front.</li>
            <li>Lower body by bending elbows, press up.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t let shoulders shrug.</li>
          </ul>
        </div>`,
      // Shoulders
      'overhead-press': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Overhead Press - How to</h3>
          <ol>
            <li>Stand or sit, hold barbell at shoulder level.</li>
            <li>Press bar overhead until arms are straight.</li>
            <li>Lower bar to shoulders.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep core tight.</li>
          </ul>
        </div>`,
      'lateral-raises': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Lateral Raises - How to</h3>
          <ol>
            <li>Stand, hold dumbbells at sides.</li>
            <li>Raise arms out to sides to shoulder height.</li>
            <li>Lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t swing body.</li>
          </ul>
        </div>`,
      'front-raises': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Front Raises - How to</h3>
          <ol>
            <li>Stand, hold dumbbells in front of thighs.</li>
            <li>Raise arms forward to shoulder height.</li>
            <li>Lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep core tight.</li>
          </ul>
        </div>`,
      'rear-delt-fly': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Rear Delt Fly - How to</h3>
          <ol>
            <li>Bend hips, hold dumbbells under chest.</li>
            <li>Lift arms up/out, squeezing rear delts.</li>
            <li>Lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t use momentum.</li>
          </ul>
        </div>`,
      'arnold-press': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Arnold Press - How to</h3>
          <ol>
            <li>Sit, hold dumbbells in front of shoulders, palms facing you.</li>
            <li>Rotate palms outward, press dumbbells overhead.</li>
            <li>Lower, rotating palms back in.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep elbows under wrists.</li>
          </ul>
        </div>`,
      // Chest
      'barbell-bench-press': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Barbell Bench Press - How to</h3>
          <ol>
            <li>Lie on bench, grip barbell shoulder-width.</li>
            <li>Lower bar to chest, press up to straight arms.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep feet flat.</li>
          </ul>
        </div>`,
      'dumbbell-bench-press': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Dumbbell Bench Press - How to</h3>
          <ol>
            <li>Lie on bench, hold dumbbells at chest.</li>
            <li>Press dumbbells up, lower under control.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t flare elbows too much.</li>
          </ul>
        </div>`,
      'incline-bench-press': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Incline Bench Press - How to</h3>
          <ol>
            <li>Set bench at 30-45° incline, lie back, grip bar or dumbbells.</li>
            <li>Lower to upper chest, press up.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Control pace.</li>
          </ul>
        </div>`,
      'chest-fly': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Chest Fly - How to</h3>
          <ol>
            <li>Lie on bench, hold dumbbells above chest.</li>
            <li>Lower arms out to sides, slight bend in elbows.</li>
            <li>Bring dumbbells back together over chest.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don’t overstretch at the bottom.</li>
          </ul>
        </div>`,
      'push-ups': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Push-Ups - How to</h3>
          <ol>
            <li>Place hands slightly wider than shoulders, feet together.</li>
            <li>Lower chest to floor, press up to straight arms.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep body straight.</li>
          </ul>
        </div>`,
      // Back
      'pull-ups': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Pull-Ups - How to</h3>
          <ol>
            <li>Grip pull-up bar with palms away, hands wider than shoulders.</li>
            <li>Hang arms fully extended.</li>
            <li>Pull chest to bar, squeeze back muscles.</li>
            <li>Lower until arms are straight.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't swing body; control movement.</li>
          </ul>
        </div>`,
      'lat-pulldown': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Lat Pulldown - How to</h3>
          <ol>
            <li>Sit at machine, grip bar wider than shoulders.</li>
            <li>Pull bar to chest, squeeze shoulder blades.</li>
            <li>Release slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't lean back excessively.</li>
          </ul>
        </div>`,
      'barbell-rows': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Barbell Rows - How to</h3>
          <ol>
            <li>Stand feet shoulder-width, hold barbell overhand.</li>
            <li>Bend at hips, keep back straight, bar hanging.</li>
            <li>Pull bar to lower chest, squeeze back.</li>
            <li>Lower bar under control.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't round your back.</li>
          </ul>
        </div>`,
      'seated-cable-rows': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Seated Cable Rows - How to</h3>
          <ol>
            <li>Sit at cable row machine, grip handles.</li>
            <li>Pull handles to stomach, squeeze back.</li>
            <li>Release slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't round back.</li>
          </ul>
        </div>`,
      't-bar-rows': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">T-Bar Rows - How to</h3>
          <ol>
            <li>Stand over T-bar, grip handles, bend at hips.</li>
            <li>Pull bar to chest, squeeze shoulder blades.</li>
            <li>Lower under control.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't jerk weight.</li>
          </ul>
        </div>`,
      'single-arm-dumbbell-rows': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Single-Arm Dumbbell Rows - How to</h3>
          <ol>
            <li>Kneel on bench, other foot on floor.</li>
            <li>Hold dumbbell with free hand, arm extended.</li>
            <li>Row dumbbell to hip, squeeze back.</li>
            <li>Lower slowly, repeat.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't round your back.</li>
          </ul>
        </div>`,
      'straight-arm-pulldown': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Straight-Arm Pulldown - How to</h3>
          <ol>
            <li>Stand facing cable machine, grip bar or rope.</li>
            <li>Keep arms straight, pull bar down to thighs.</li>
            <li>Squeeze lats, let bar rise slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't bend elbows.</li>
          </ul>
        </div>`,
      // Legs
      'barbell-squats': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Barbell Squats - How to</h3>
          <ol>
            <li>Stand with barbell on upper back, feet shoulder-width.</li>
            <li>Bend knees/hips, lower until thighs parallel to floor.</li>
            <li>Press back up to standing.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep chest up.</li>
          </ul>
        </div>`,
      'leg-press': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Leg Press - How to</h3>
          <ol>
            <li>Sit in leg press machine, feet on platform shoulder-width.</li>
            <li>Lower platform by bending knees, press back up.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't lock knees at top.</li>
          </ul>
        </div>`,
      'lunges': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Lunges - How to</h3>
          <ol>
            <li>Stand tall, step forward with one leg.</li>
            <li>Lower body until both knees bent at 90°.</li>
            <li>Push back to standing, repeat other leg.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Keep torso upright.</li>
          </ul>
        </div>`,
      'leg-extension': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Leg Extension - How to</h3>
          <ol>
            <li>Sit in leg extension machine, pad just above ankles.</li>
            <li>Extend legs, pause, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't lock knees.</li>
          </ul>
        </div>`,
      'leg-curl': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Leg Curl - How to</h3>
          <ol>
            <li>Lie face down on leg curl machine, pad above heels.</li>
            <li>Curl pad up, squeeze hamstrings, lower slowly.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Don't lift hips off pad.</li>
          </ul>
        </div>`,
      'standing-calf-raises': `
        <div class="howto-slide">
          <button class="howto-close" onclick="closeHowto()">Close</button>
          <h3 class="howto-title">Standing Calf Raises - How to</h3>
          <ol>
            <li>Stand on platform, balls of feet on edge.</li>
            <li>Raise heels as high as possible, lower below platform.</li>
          </ol>
          <b>Tips:</b>
          <ul>
            <li>Pause at top for squeeze.</li>
          </ul>
        </div>`
    };

    function showExercises(muscle) {
      // Hide grid and any slides
      document.getElementById('muscleGrid').classList.add('hidden');
      document.getElementById('howtoSection').innerHTML = '';
      document.getElementById('dietSection').classList.add('hidden');
      // Get muscle data
      const m = muscleData[muscle];
      if (!m) return;
      // Build exercise list
      let html = `<h2 class="exercise-title">${m.title}</h2>
        <p>${m.info}</p>
        <ul class="exercise-ul">`;
      for (const ex of m.exercises) {
        html += `<li>${ex.name}
          <button class="howto-link" onclick="showHowto('${ex.key}')">How to</button>
        </li>`;
      }
      html += `</ul>
        <button class="back-link" onclick="showMuscleGrid()">← Back to muscle groups</button>`;
      document.getElementById('exerciseSection').innerHTML = html;
      document.getElementById('exerciseSection').classList.remove('hidden');
    }
    function showMuscleGrid() {
      document.getElementById('muscleGrid').classList.remove('hidden');
      document.getElementById('exerciseSection').classList.add('hidden');
      document.getElementById('howtoSection').innerHTML = '';
      document.getElementById('dietSection').classList.add('hidden');
      document.getElementById('bmiResult').innerHTML = '';
      document.getElementById('dietFoodList').innerHTML = '';
      document.getElementById('heightInput').value = '';
      document.getElementById('weightInput').value = '';
    }
    function showHowto(exerciseKey) {
      document.getElementById('howtoSection').innerHTML = howtoContent[exerciseKey] || '<div class="howto-slide">Instructions not added yet.</div>';
      window.scrollTo({top:document.getElementById('howtoSection').offsetTop-50, behavior:'smooth'});
    }
    function closeHowto() {
      document.getElementById('howtoSection').innerHTML = '';
    }
    function showDiet() {
      document.getElementById('muscleGrid').classList.add('hidden');
      document.getElementById('exerciseSection').classList.add('hidden');
      document.getElementById('dietSection').classList.remove('hidden');
      document.getElementById('howtoSection').innerHTML = '';
      document.getElementById('bmiResult').innerHTML = '';
      document.getElementById('dietFoodList').innerHTML = '';
      document.getElementById('heightInput').value = '';
      document.getElementById('weightInput').value = '';
    }
    function calcBMI() {
      let h = parseFloat(document.getElementById('heightInput').value);
      let w = parseFloat(document.getElementById('weightInput').value);
      if (!h || !w || h < 100 || w < 30) {
        document.getElementById('bmiResult').innerHTML = "<span style='color:#ff5454'>Please enter valid height and weight.</span>";
        document.getElementById('dietFoodList').innerHTML = '';
        return;
      }
      let hm = h / 100;
      let bmi = w / (hm * hm);
      let cat = '';
      let catText = '';
      bmi = Math.round(bmi * 10) / 10;
      if (bmi < 18.5) {
        cat = 'underweight';
        catText = 'Underweight';
      } else if (bmi < 25) {
        cat = 'normal';
        catText = 'Normal weight';
      } else if (bmi < 30) {
        cat = 'overweight';
        catText = 'Overweight';
      } else {
        cat = 'obese';
        catText = 'Obese';
      }
      document.getElementById('bmiResult').innerHTML = `<b>Your BMI:</b> ${bmi} <br><b>Category:</b> <span style="color:#00ffe7">${catText}</span>`;
      let d = dietData[cat];
      if (d) {
        let flist = '<ul>';
        for (let f of d.foods) flist += `<li>${f}</li>`;
        flist += '</ul>';
        document.getElementById('dietFoodList').innerHTML = `
          <h4>${d.title} - Recommended Foods:</h4>
          ${flist}
          <b>Tips:</b> ${d.tips}
        `;
      } else {
        document.getElementById('dietFoodList').innerHTML = '';
      }
    }
  </script>
</body>
</html>
