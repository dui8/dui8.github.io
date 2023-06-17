게임 프로그래머를 향하기 위한 길
=============

유니티
--------


[UNITY install](https://unity.com/kr/products/unity-pro?utm_source=google&utm_medium=cpc&utm_campaign=cc_dd_unitypro_apac_kr_kr_pu_sem-gg_acquisition_br-pr_2023-04_unitypro-bofu_cc3022&utm_content=&utm_term=%7Bkeyword%7D&&&&&gad=1&gclid=EAIaIQobChMI0r65zdHJ_wIVi6iWCh2jHwpPEAAYASAAEgKfNvD_BwE&gclsrc=aw.ds, "UNITY install link")

1.기초 유니티 무브먼트 명령어
```
Rigidbody rigid;

void Start() {
    rigid = GetComponent<Rigidbody>();
}

void FixedUpdate() {
    Vector3 vec = new vec())
    rigid.AddForce(vec, ForceMode.Impulse);
}
```
2.몬스터 간단한 ai 개발 스크립트
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyMove : MonoBehaviour
{
    Rigidbody2D rigid;
    Animator anim;
    SpriteRenderer spriteRenderer;
    BoxCollider2D boxcollider;

    public int nextMove;

    void Awake()
    {
        rigid = GetComponent<Rigidbody2D>();
        anim = GetComponent<Animator>();
        spriteRenderer = GetComponent<SpriteRenderer>();
        boxcollider = GetComponent<BoxCollider2D>();
        Invoke("Think", 5);
    }

    void FixedUpdate()
    {
        //move
        rigid.velocity = new Vector2(nextMove , rigid.velocity.y);

        //Platform Check;
        Vector2 frontVec = new Vector2(rigid.position.x + nextMove * 0.2f, rigid.position.y);
        Debug.DrawRay(frontVec, Vector3.down, new Color(0, 1, 0));
        RaycastHit2D rayHit = Physics2D.Raycast(frontVec, Vector3.down, 1, LayerMask.GetMask("Platform"));
        if (rayHit.collider == null) {
            Turn();
        }
    }
    
    //Think
    void Think()
    {
        //Set Next Active
        nextMove = Random.Range(-1, 2);

        //Sprite Animation
        anim.SetInteger("WalkSpeed", nextMove);

        //Flip Sprite
        if(nextMove != 0)
            spriteRenderer.flipX = nextMove == 1;

        //Recursive
        float nextThinkTime = Random.Range(2f, 5f);
        Invoke("Think", nextThinkTime);
    }

    void Turn()
    {
        nextMove = nextMove * -1;
        spriteRenderer.flipX = nextMove == 1;

        CancelInvoke();
        Invoke("Think", 5);
    }

    public void OnDamaged()
    {
        //Sprite Alpha
        spriteRenderer.color = new Color(1, 1, 1, 0.4f);
        //Sprite Flip Y
        spriteRenderer.flipY = true;
        //Collider Disable
        boxcollider.enabled = false;
        //Die Effect Jump
        rigid.AddForce(Vector2.up * 5, ForceMode2D.Impulse);
        //Destroy
        Invoke("DeActive", 5);

    }

    void DeActive()
    {
        gameObject.SetActive(false);
    }
}
```