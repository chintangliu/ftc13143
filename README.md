# ftc13143
Teamcode for Warrior Machine, 13143
package org.firstinspires.ftc.teamcode;

import com.qualcomm.robotcore.eventloop.opmode.OpMode;
import com.qualcomm.robotcore.eventloop.opmode.TeleOp;
import com.qualcomm.robotcore.hardware.DcMotor;
import com.qualcomm.robotcore.hardware.Servo;
import com.qualcomm.robotcore.hardware.CRServo;
/**
 * created by Eric Liu on 10/15/2017.
 */

@TeleOp(name="TeleOp1", group ="Opmode")

public class TeleOp1 extends OpMode {

    // DriveTrain Motor Declaration

    DcMotor FrontLeft;
    DcMotor FrontRight;
    DcMotor BackLeft;
    DcMotor BackRight;
    CRServo Gripper;
    CRServo Jewel;
    Servo Balance;


    @Override
    public void init() {
        //Driving Motors
        FrontRight = hardwareMap.dcMotor.get("fr");
        FrontLeft = hardwareMap.dcMotor.get("fl");
        BackRight = hardwareMap.dcMotor.get("br");
        BackLeft = hardwareMap.dcMotor.get("bl");
        FrontRight.setDirection(DcMotor.Direction.REVERSE);
        BackRight.setDirection(DcMotor.Direction.REVERSE);
        //Servos
        Gripper = hardwareMap.crservo.get("grip");
        Jewel = hardwareMap.crservo.get("jewel");
        Balance = hardwareMap.servo.get("bal");



    }

    @Override
    public void loop() {

        float lefty1 = -gamepad1.left_stick_y;
        float righty1 = -gamepad1.right_stick_y;

        // Drive Train  *** Left  WheelsGamepad 1 Left Stick
        //              *** Right WheelsGamepad 1 Right Stick

        if (lefty1 < -.2 || lefty1 > .2) {
            FrontLeft.setPower(lefty1);
            BackLeft.setPower(lefty1);
        } else {
            for (int i = 1; i > .0001; i *= .1) {
                FrontLeft.setPower(lefty1 * i);
                BackLeft.setPower(lefty1 * i);
            }
        }
        if (righty1 < -.2 || righty1 > .2) {
            FrontRight.setPower(righty1);
            BackRight.setPower(righty1);
        } else {
            for (int i = 1; i > .0001; i *= .1) {
                FrontRight.setPower(righty1 * i);
                BackRight.setPower(righty1 * i);
            }
        }
    }
