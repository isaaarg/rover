# rover
// Rover Object Goes Here
// ======================
//1
const North = "North";
const South = "South";
const West = "West";
const East = "East";

class Rover {

    constructor(direction=North, row=0, column=0) {
        this.direction=direction;
        this.row=row;
        this.column=column;
        this.travelLog = [];
    }

    turnLeft() {
        if (this.direction === North) {
            this.direction = West;
        }
        else if (this.direction === South) {
            this.direction = East;
        }
        else if (this.direction === West){
            this.direction = South;
        }
        else if (this.direction === East){
            this.direction = North;
        }

    }

    turnRight() {
        if (this.direction === North) {
            this.direction = East;
        }
        else if (this.direction === South) {
            this.direction = West;
        }
        else if (this.direction === West) {
            this.direction = North;
        }
        else if (this.direction === East) {
            this.direction = South;
        }
    }

    moveForward(n=1) {
      this.travelLog.push([this.row, this.column]);
        switch (this.direction) {
          case North:
            this.row -= n;
            break;
          case South:
            this.row += n;
            break;
          case West:
            this.column -= n;
            break;
          case East:
            this.column += n;
            break;
        }
    }

    move(steps) {
        for (var i = 0; i < steps.length; i++) {
          const step = steps[i];
          switch (steps[i]) {
            case "r":
              this.turnRight();
              break;
            case "l":
              this.turnLeft();
              break;
            case "f":
              this.moveForward();
              break;
          }
        }
    }
  }
