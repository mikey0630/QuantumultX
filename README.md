// 获取输入数据，假设获取到的数组数据依次为GN、IOS、光圈值、拍摄距离
const inputs = $input;
const GN = parseFloat(inputs[0]);
const IOS = parseFloat(inputs[1]);
const aperture = parseFloat(inputs[2]);
const distance = parseFloat(inputs[3]);

// 计算调整后的闪光指数需求
const adjustedGN = GN * Math.sqrt(100 / IOS);

let flashPower;
if (aperture * distance >= adjustedGN) {
    flashPower = "1";
} else if (aperture * distance >= adjustedGN / 2) {
    flashPower = "1/2";
} else if (aperture * distance >= adjustedGN / 4) {
    flashPower = "1/4";
} else if (aperture * distance >= adjustedGN / (2 * Math.sqrt(2))) {
    flashPower = "1/8";
} else {
    flashPower = "1/16";
}

$output = flashPower;
