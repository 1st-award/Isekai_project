var cols, rows;
var scl = 20;
var w = 2400;
var h = 1200;
var terrain = [];
var framePreset = 0;
var moonlight = 0;
var cameraPosX, cameraPosY;
var flightPosX, flightPosY;
var flyingSpeed = 0;
var mode;
var score = 0;
let flightShootDelay = 0;
let countShoot = 0;
let enemy = 0;
let cameraSpeed = 0;
let font;
let enemyBullet = [];
let flightShoot = [];
const FRAME_RATE = 60;
const SPACEBAR = 32;
const MODE_GAME_TITLE = 0;
const MODE_IN_GAME = 1;
const MODE_GAME_OVER = 2;
const ENEMY_DIE = 0;
const ENEMY_SURVIVE = 1;
const MODE_GAME_WIN = 3;

function preload() {
    font = loadFont('malgunsl.ttf');
    img1 = loadImage('https://c.tenor.com/eHHdbBT9us0AAAAC/%ED%8F%AD%EB%B0%9C-%EC%8B%AC%EC%98%81.gif');
    img2 = loadImage('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQN28TXtx8G6hh3wcf5npDYzDRx9aBWVkM-gQ&usqp=CAU');
    img3 = loadImage('data:image/jpeg;base64,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');
}

function setup() {
    mode = MODE_GAME_TITLE; //initialy the game has not started
    createCanvas(600, 600, WEBGL);
    textFont(font);
    textAlign(CENTER);
    camera1 = createCamera();
    camera = createCamera();
    cols = w / scl;
    rows = h / scl;
    // 2차원 배열 초기화
    for (var x = 0; x < cols; x++) {
        terrain[x] = [];
        for (var y = 0; y < rows; y++) {
            terrain[x][y] = 0; //specify a default value for now
        }
    }
    noStroke();
    // 비행기 위치 초기화
    flightPosX = 300 - width / 2;
    flightPosY = height / 2 - 150;
    cameraPosX = flightPosX;
    cameraPosY = flightPosY / 10;
    for (let i = 0; i < 200; i++) {
        enemyBullet[i] = new EnemyBullet();
    }
    enemy = new EnemyShooter();
    for (let i = 0; i < 10; i++) {
        flightShoot[i] = new FlightShoot();
    }
}

function draw() {
    clear();
    if (keyCode === ENTER) {
        mode = MODE_IN_GAME;
        enemy.life = 30;
        enemy.state = ENEMY_SURVIVE;
        score = 0;
        setCamera(camera);
        flightPosX = 0;
        flightPosY = 0;
        enemy.x = w / 2;
        for (let i = 0; i < 200; i++) {
            enemyBullet[i].x = 0;
            enemyBullet[i].y = 0;
        }
        for (let i = 0; i < 10; i++) {
            flightShoot[i].x = -0;
            flightShoot[i].y = -10000;
        }
    }
    if (mode == MODE_GAME_TITLE) {
        background(255);
        textSize(30);
        fill(0);
        text('[여기에 제목을 입력]', 0, -80);
        textSize(48);
        text('Press Enter to start', 0, 120);
    }
    if (mode == MODE_GAME_OVER) {
        setCamera(camera1);
        image(img1, -300, -400, 600, 600);
        image(img2, -150, -100, 400, 100);
        text(score, 0, 120);
    }
    if (mode == MODE_GAME_WIN){
      setCamera(camera1);
      image(img3, -300, -400, 600, 600);
      textSize(50);
      fill(255,255,0);
      text('승리', 0, 120);
    }
    if (mode == MODE_IN_GAME) {
        score++;
        framePreset = frameCount / FRAME_RATE;
        moonlight = framePreset / 3;
        if (sin(framePreset) > 0) {
            background(0);
        } else {
            background(80, 188, 223);
        }
        // 산 높이 및 산 이동 속도 설정
        flyingSpeed -= 0.01 + map(cameraSpeed, 0, 50, 0.01, 0.09);
        setMountain(flyingSpeed);
        translate(0, 50);
        rotateX(PI / 3);
        // 카메라 위치 설정 및 각도 설정
        camera.lookAt(flightPosX, flightPosY - 90, 200);
        camera.setPosition(flightPosX + cameraPosX, (flightPosY + cameraPosY) + cameraSpeed - 90, 266 + cameraSpeed);
        translate(-w / 2, -h / 2);
        // 산 생성
        makeMountain();
        push();
        // 해와 달 생성
        makeSun(framePreset);
        makeMoon(framePreset, moonlight);
        pop();
        /* 적이 살아 있을 시 */
        if (enemy.state != 0) {
            for (let j = 0; j < 200; j++) {
                enemyBullet[j].delay = j;
                enemyBullet[j].move(map(j, 0, 100, 0, PI));
                enemyBullet[j].display();
            }
            enemy.move(framePreset * 6);
            enemy.display();
        }
        translate(w / 2, h / 2);
        /* 비행기 위치 이동 translate */
        push();
        translate(flightPosX, flightPosY, 200);
        flight();
        pop();
        /* 스페이스 바를 누를 시 총알이 발사 */
        if (keyIsDown(SPACEBAR)) {
            if (flightShootDelay <= 0) {
                flightShootDelay = 30;
                flightShoot[countShoot % 10].x = flightPosX;
                flightShoot[countShoot % 10].y = flightPosY;
                countShoot++;
            }
        }
        /* 총알 출력 */
        for (let i = 0; i < 10; i++) {
            push();
            flightShoot[i].display();
            pop();
        }
        flightShootDelay--;
    }
}

function setMountain(_flyingSpeed) {
    /* 산 높이를 설정하는 함수 */
    var yoff = _flyingSpeed;
    for (var y = 0; y < rows; y++) {
        var xoff = 0;
        for (var x = 0; x < cols; x++) {
            terrain[x][y] = map(noise(xoff, yoff), 0, 1, -100, 100);
            xoff += 0.5;
        }
        yoff += 0.2;
    }
}

function makeMountain() {
    /* 산 만드는 함수 */
    for (var y = 0; y < rows - 1; y++) {
        beginShape(TRIANGLE_STRIP);
        for (var x = 0; x < cols; x++) {
            let v = terrain[x][y];
            v = map(v, -100, 100, 0, 255);
            fill(v - 64, v - 32, v);
            vertex(x * scl, y * scl, terrain[x][y]);
            vertex(x * scl, (y + 1) * scl, terrain[x][y + 1]);
        }
        endShape();
    }
}

function makeSun(_framePreset) {
    /* 태양 만드는 함수 */
    translate(w / 2 - cos(_framePreset) * 800, 0, -sin(_framePreset) * 260);  //sun
    push();
    ambientLight(50);
    pointLight(255, 255, 255, 0, 0, 50);
    specularMaterial(255, 0, 0);
    sphere(50);
    pop();
}

function makeMoon(_framePreset, _moonlight) {
    /* 달 만드는 함수 */
    translate(cos(_framePreset) * 1600, 0, sin(_framePreset) * 520);    //moon
    pointLight(250, 250, 250, 1800 - ((_moonlight * 900) % 3600), -400, 50);
    fill(255, 255, 0);
    sphere(50);
}

function flight() {
    /* 비행기 키보드 이동 및 생성 함수 */
    flightKeyPressed();

    fill(125);
    triangle(-5, 2, 0, -3, 5, 2);
    triangle(-5, 2, -2.5, 2, -3.75, 3.75);
    fill(0);
    triangle(-2.5, 2, 0, 2, -1.25, 2.75);
    triangle(0, 2, 2.5, 2, 1.25, 2.75);
    fill(125);
    triangle(2.5, 2, 5, 2, 3.75, 3.75);
    noFill();
}

function flightKeyPressed() {
    /* 비행기 및 카메라 조절 함수 */
    if (keyIsDown(UP_ARROW)) {
        cameraSpeed += 2;
        flightPosY -= 10;
        cameraPosY -= 10;
    }
    if (keyIsDown(DOWN_ARROW)) {
        cameraSpeed -= 2;
        flightPosY += 10;
        cameraPosY += 10;
    }
    if (keyIsDown(LEFT_ARROW)) {
        rotateY(-PI / 3);
        flightPosX -= 10;
        cameraPosX -= 10;
    }
    if (keyIsDown(RIGHT_ARROW)) {
        rotateY(PI / 3);
        flightPosX += 10;
        cameraPosX += 10;
    }
    cameraRollBack();
    limitFlightField(flightPosX, flightPosY);
    limitCamera(cameraPosX, cameraPosY);
}

function limitFlightField(_flightPosX, _flightPosY) {
    /* 비행기가 움직일 수 있는 범위를 제한합니다 */
    limitX = 1080;
    limitY = 330;
    if (_flightPosX > limitX) {
        flightPosX = limitX;
    } else if (_flightPosX < -limitX) {
        flightPosX = -limitX;
    }
    if (_flightPosY > limitY) {
        flightPosY = limitY;
    } else if (_flightPosY < -limitY) {
        flightPosY = -limitY;
    }
}

function limitCamera(_cameraPosX, _cameraPosY) {
    /* 카메라 이동 범위를 제한합니다. */
    var limitX = 25;
    var limitY = 150;
    if (_cameraPosX >= limitX) {
        cameraPosX = limitX;
    } else if (_cameraPosX < -limitX) {
        cameraPosX = -limitX;
    }
    if (_cameraPosY > limitY || _cameraPosY <= limitY) {
        cameraPosY = limitY;
    }

    if (cameraSpeed > 50) {
        cameraSpeed = 50;
    } else if (cameraSpeed < 0) {
        cameraSpeed = 0;
    }
}

function cameraRollBack() {
    /* 카메라를 원래대로 복귀시킵니다 */
    if (cameraPosX > 0) {
        cameraPosX--;
    } else if (cameraPosX < 0) {
        cameraPosX++;
    }

    if (cameraSpeed > 0) {
        cameraSpeed--;
    } else if (cameraSpeed < 0) {
        cameraSpeed++;
    }
}

class FlightShoot {
    /* 유저 총알 */
    constructor() {
        this.x = 0;
        this.y = 0;
        this.speed = 5;
    }

    display() {
        push();
        translate(this.x, this.y, 200);
        if (abs(this.x - enemy.x + w / 2) < 40 && this.y == enemy.y) {
            enemy.life--;
        }
        this.y -= this.speed;
        fill(0, 255, 0);
        box(2);
        pop();
    }
}

class EnemyBullet {
    /* 적 총알 */
    constructor() {
        this.x = w / 2;
        this.y = -100;
        this.speed = 10;
        this.time = 0;
        this.delay = 0;
    }

    move(value) {
        if (this.time > this.delay) {
            this.x += sin(value) * this.speed;
            this.y += 10;
        }
        this.time++;
    }

    display() {
        push();
        translate(this.x, this.y, 200);
        if (abs(this.x - 1200 - flightPosX) < 4 && abs(this.y - 600 - flightPosY) < 4) {
            mode = MODE_GAME_OVER;
        }
        if (this.time > 200 + this.delay) {
            this.x = w / 2;
            this.y = -100;
            this.time = this.delay;
        }
        fill(255, 255, 0);
        sphere(4);
        pop();
    }
}

class EnemyShooter {
    /* 적 */
    constructor() {
        this.x = w / 2;
        this.y = -100;
        this.life = 30;
        this.state = ENEMY_SURVIVE;
    }

    move(value) {
        this.x += sin(value) * 2;
    }

    display() {
        push();
        translate(this.x, this.y, 200);
        if (this.life == 1) {
            fill(0);
            enemy.state = ENEMY_DIE;
            mode = MODE_GAME_WIN;
        }
        if (this.life <= 3 && this.life > 1) {
            if (frameCount % 2 == 1) {
                fill(127);
            }
            if (frameCount % 2 == 0) {
                fill(255);
            }
        }
        if (this.life <= 10 && this.life > 3) {
            fill(255, 0, 0);
        }
        if (this.life > 10) {
            fill(255);
        }
        torus(40);
        pop();
    }
}
