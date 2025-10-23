```CPP
class Player
{
public:
    static const int MAX_HEALTH = 100;

    Player(const std::string& name);
    ~Player();

    void Update(float deltaTime);
    void Render() const;
    void TakeDamage(int amount);

protected:
    Vec2 m_position;
    float m_speed;

    void Move(const Vec2& direction);
    void HandleCollision();

private:
    int m_health;
    std::string m_name;

    void Regenerate();
    void CheckStatus();
};
```