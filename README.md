# CPS (clicks per second) test
**1)** **Dual CPS Test (Left & Right Click)**
A lightweight, web-based Clicks Per Second (CPS) tester designed to measure your left-click and right-click speeds independently. This is a perfect tool for gamers (especially Minecraft PVPers) to track their butterfly clicking, jitter clicking, or drag clicking speeds.

**2)** **Features**
Separate Tracking: Independent, split-screen zones for both Left Click and Right Click monitoring.

Instant CPS Calculation: Tracks and updates your active CPS in real-time as the timer ticks down.

Flexible Durations: Quick-select presets for 1s, 5s, 10s, 30s, and 60s, along with a Custom Time input for personalized endurance tests.

Anti-Context-Menu: Prevents the standard browser right-click menu from opening, allowing smooth, continuous right-click speed testing.

Modern UI: A clean, scannable dark-themed interface built using vanilla HTML, CSS, and JavaScript.

**3)** **How to Use**
Choose your time: Click one of the quick preset buttons or type a custom number of seconds and hit Set.

Start clicking: Hover your mouse over either the LEFT CLICK or RIGHT CLICK box and start clicking. The timer will automatically trigger on your very first click! 

Check your results: Watch your live CPS change, and get a complete scoreboard alert summary once the countdown hitting zero.

Reset: Use the Reset CPS button to clear the board and start fresh.

**4)** **JavaScript Architecture & Functions**
The logic relies entirely on pure vanilla JavaScript (EventListeners, setInterval, and DOM manipulation). Here is a breakdown of the core functions driving the application:

 Timer & State Management
setTime(t): Updates the test duration based on the quick-select preset buttons (1s, 5s, etc.). It safely blocks duration changes if a test is currently running.

setCustom(): Reads the numeric value from the custom input field, validates that it is a positive number, and sets it as the active test duration.

startTest(): Initializes the tracking state. It triggers the countdown sequence using setInterval(), ticking down every 1,000 milliseconds (1 second) and refreshing the live scoreboard.

endTest(): Clears the background interval timer, stops click tracking, computes final speeds, and fires a clean summary popup detailing your final performance metrics.

resetTest(): Acts as a hard clear. It instantly wipes any active interval timers, zeros out the tracking coordinates, and restores the UI display to its default state.

**5)** **Live Calculation & UI SyncingupdateUI()**
Handles direct DOM rendering for the pure mechanical click counters, injecting the updated raw totals into the viewport.updateCPS(): Dynamically calculates your performance by tracking elapsed time. It divides clicks by elapsed seconds to output smooth decimal speeds in real time, preventing mathematical division-by-zero crashes at start line.

**6)** **Input Handling & Event Bindings**
pointerdown Listeners: Bound directly to the interactive zones. Uses explicit pointer inspections (e.pointerType === "mouse") and button bitmasks (e.buttons === 1 for left, 2 for right) to filter out fake clicks or touchscreen taps. It automatically wakes up startTest() on your very first strike.

contextmenu Blocker: Intercepts and completely neutralizes default right-click browser prompts (e.preventDefault()), allowing uninterrupted performance tracking.
