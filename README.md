use GuzzleHttp\Client;

class YOUR_MODEL extends CI_Model {

    private $_client;

    public function __construct()
    {
        $this->_client = new Client([
            'base_uri' => 'http://localhost/q-tech-api/YOURPAATH/',
            'auth'  => ['YOUR USERNAME', 'PASSWORD']
        ]);
    }

    public function listing_users()
    {

        $response = $this->_client->request(
            'GET',
            'YOUR PATH',
            [
                'query' => [
                    'q-tech-KEY'    => 'YOURKEY'
                ]
            ]
        );

        $result = json_decode($response->getBody()->getContents(), true);
        return $result['apivariable'];
    }
}
