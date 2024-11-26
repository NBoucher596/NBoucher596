```cpp
public void AITankMovement()
{
    Vector3 playerPos = m_Tanks[0].m_Instance.transform.position;

    for (int i = 1; i < m_Tanks.Length; i++)
    {
        shootingUpdate(m_Tanks[i]);

        m_health = m_Tanks[i].m_Instance.GetComponent<TankHealth>();

        m_Rigidbody = m_Tanks[i].m_Instance.GetComponent<Rigidbody>();

        if (m_Tanks[i].isEnabled)
        {
            Vector3 enemyPos = m_Tanks[i].m_Instance.transform.position;

            List<Ray> moveRays = new List<Ray>(90);

            Ray arrRay = new Ray();
            arrRay.origin = new Vector3(enemyPos.x, 1f, enemyPos.z);

            for (int j = 0; j < 90; j++)
            {
                arrRay.direction = Quaternion.AngleAxis(-45f + j, transform.up) * m_Tanks[i].m_Instance.transform.forward;
                moveRays.Add(arrRay);
            }

            Rigidbody m_Rigidbody = m_Tanks[i].m_Instance.GetComponent<Rigidbody>();

            bool hasTurned = new bool();
            bool hasShot = new bool();

            RaycastHit terrain = new RaycastHit();
            RaycastHit player = new RaycastHit();

            for (int k = 0; k < moveRays.Count; k++)
            {
                if (!hasTurned)
                {
                    if (Physics.Raycast(moveRays.ElementAt(k), out terrain, 5f) && terrain.transform.tag != "SpawnPoint")
                    {
                        hasTurned = true;
                        if ((-45f + k) < 0)
                        {
                            turn(1f, m_Tanks[i]);
                        }
                        else if ((-45f + k) > 0)
                        {
                            turn(-1f, m_Tanks[i]);
                        }
                    }
                }
                if (!hasShot && !m_health.m_Dead)
                {
                    if (Physics.Raycast(moveRays.ElementAt(k), out player, 20f) && player.transform.tag == "Player")
                    {
                        hasShot = true;
                        m_Tanks[i].m_Instance.transform.LookAt(playerPos);
                        shootingUpdate(m_Tanks[i]);
                        m_shooting.setLaunchForce(15f);
                        if (time % 480f == 0f)
                        {
                            m_shooting.AIFire();
                        }
                        time++;
                    }
                }
            }
            hasTurned = false;
            hasShot = false;
            move(1f, m_Tanks[i]);
        }
    }
}
```