Void 종류
=====================
**void Awake()  #게임 오브젝트 생성할 때, 최초 실행**

**void OnEnable  #게임 오브젝트가 활성화 되었을 때**

**void Start()  #업데이트 시작 직전, 최초 실행**

**void FixedUpdate()  #물리 연산 업데이트**

**void Update()  #게임 로직 업데이트**

**void LateUpdate  #모든 업데이트 끝난 후**

**void OnDestroy  #게임 오브젝트가 삭제될 때**

//실제 물리적인 충돌로 발생하는 이벤트
----------

**void OnCollisionEnter(Collision collision)**

**void OnCollisionStay(Collision collision)**

**void OnCollisionExit(Collision collision)**

//콜라이더 충돌로 발생하는 이벤트
---------

**void OnTriggerEnter(Collider other)**

**void OnTriggerStay(Collider other)**

**void OnTriggerExit(Collider other)**