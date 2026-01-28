# Auxiliary Equipment Tracking System

A simple web-based tracking system for managing blender and grinder equipment during cleaning and changeover operations.

## Overview

This system helps two key roles manage auxiliary equipment (blenders and grinders) through their lifecycle:
- **Changeover Operators**: Move equipment between machines and cleaning areas
- **Cleaning Operators**: Clean equipment and return them to the already cleaned area

## Features

### For Changeover Operators

1. **Send Equipment to Cleaning**
   - Check cleaning requirements for current machine/order
   - Get routing based on cleaning type:
     - **24H Reuse**: Direct transfer to next machine (no cleaning needed)
     - **Light Cleaning**: Route to light cleaning area
     - **Deep Cleaning**: Route to deep cleaning area

2. **Retrieve Cleaned Equipment**
   - Find exact bin location in Already Cleaned (AC) area
   - Search by machine number or order number
   - See equipment details and completion time

### For Cleaning Operators

1. **View Cleaning Queue**
   - See prioritized list of equipment to clean
   - Know cleaning type for each item
   - See destination bin information

2. **Complete Cleaning Tasks**
   - Select AC bin where equipment is returned
   - Mark task as completed
   - Remove from queue

## How to Use

### Installation

1. Download the `equipment-tracking.html` file
2. Open it in any modern web browser (Chrome, Firefox, Safari, Edge)
3. No server or installation required - it runs completely in the browser

### Quick Start

1. **Select Your Role**: Click either "Changeover Operator" or "Cleaning Operator" button at the top
2. **Follow the workflow** for your role (see below)

## Testing Guide

### Test Data Available

#### For Changeover Operators - Send to Cleaning

You can test with these **machine numbers**:
- `1101` - 24H Reuse (next machine: 1105)
- `1102` - Light Cleaning (bin: LC-02)
- `1107` - 24H Reuse (next machine: 1110)
- `1203` - Light Cleaning (bin: LC-05)
- `1209` - Deep Cleaning (bin: DC-01)
- `3513` - 24H Reuse (next machine: 3518)
- `3515` - Deep Cleaning (bin: DC-03)
- `3520` - Light Cleaning (bin: LC-09)

Or these **order numbers**:
- `154238` - 24H Reuse
- `187453` - Light Cleaning
- `219867` - Deep Cleaning

#### For Changeover Operators - Retrieve Cleaned Equipment

You can test with these **machine numbers**:
- `1208` - Location: AC-08
- `1112` - Location: AC-04
- `3521` - Location: AC-03

Or these **order numbers**:
- `123456` - Location: AC-02
- `176543` - Location: AC-07

### Testing Workflows

#### Test 1: 24H Reuse Scenario

1. Switch to **Changeover Operator**
2. Select task type: "Send Equipment to Cleaning"
3. Enter machine number: `1101`
4. Click "Check Cleaning Requirements"
5. **Expected Result**: 
   - Cleaning Type: 24H Reuse (green badge)
   - Equipment: Blender BLD-025, Grinder GRD-018
   - Destination: Move directly to Machine 1105

#### Test 2: Light Cleaning Scenario

1. Switch to **Changeover Operator**
2. Select task type: "Send Equipment to Cleaning"
3. Enter machine number: `1203`
4. Click "Check Cleaning Requirements"
5. **Expected Result**:
   - Cleaning Type: Light Cleaning (yellow badge)
   - Equipment: Blender BLD-012, Grinder GRD-009
   - Destination: Light Cleaning Area, Bin LC-05

#### Test 3: Deep Cleaning Scenario

1. Switch to **Changeover Operator**
2. Select task type: "Send Equipment to Cleaning"
3. Enter order number: `219867`
4. Click "Check Cleaning Requirements"
5. **Expected Result**:
   - Cleaning Type: Deep Cleaning (red badge)
   - Equipment: Blender BLD-031, Grinder GRD-022
   - Destination: Deep Cleaning Area, Bin DC-03

#### Test 4: Retrieve Cleaned Equipment

1. Switch to **Changeover Operator**
2. Select task type: "Retrieve Cleaned Equipment"
3. Enter machine number: `1208`
4. Click "Find Equipment Location"
5. **Expected Result**:
   - Location: AC-08 (Already Cleaned Area)
   - Equipment: Blender BLD-017, Grinder GRD-014
   - Completed: 2026-01-28 09:30
   - Status: Ready for Installation

#### Test 5: Cleaning Operator Workflow

1. Switch to **Cleaning Operator**
2. **Expected Result**: See queue with 3 items prioritized
3. For the first item (Priority 1):
   - Select an AC bin from dropdown (e.g., AC-05)
   - Click "Mark as Completed"
4. **Expected Result**: Item removed from queue

#### Test 6: AC Bin Selection Validation

1. Switch to **Cleaning Operator**
2. Try to click "Mark as Completed" WITHOUT selecting an AC bin
3. **Expected Result**: Alert message "Please select an AC bin location before marking as completed"

## Understanding the System

### Cleaning Types

- **24H Reuse**: Equipment can be reused within 24 hours without cleaning. Direct transfer to next machine.
- **Light Cleaning**: Basic cleaning required. Goes to LC (Light Cleaning) bins, then to AC (Already Cleaned) bins.
- **Deep Cleaning**: Thorough cleaning required. Goes to DC (Deep Cleaning) bins, then to AC (Already Cleaned) bins.

### Bin Areas

- **LC-xx**: Light Cleaning area bins (LC-01 to LC-10)
- **DC-xx**: Deep Cleaning area bins (DC-01 to DC-10)
- **AC-xx**: Already Cleaned area bins (AC-01 to AC-10)

### Equipment Identification

- **Machine Numbers**: 4-digit format (e.g., 1101, 1203, 3515)
- **Order Numbers**: 6-digit format starting with 1 or 2 (e.g., 154238, 219867)
- **Blenders**: Format BLD-xxx (e.g., BLD-025)
- **Grinders**: Format GRD-xxx (e.g., GRD-018)

## Technical Details

- **Technology**: Pure HTML, CSS, and JavaScript
- **No Dependencies**: No external libraries or frameworks required
- **Browser Compatibility**: Works on all modern browsers
- **Data Storage**: Currently uses in-memory data (resets on page reload)

## Future Enhancements

- Real-time database integration
- QR code scanning for equipment
- User authentication
- Historical tracking and reports
- Mobile app version
- Notification system for completed tasks

## Support

For issues or questions, please open an issue on GitHub.

## License

MIT License
