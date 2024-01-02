CREATE VIEW vista_pedidos AS
SELECT * FROM pedido30_34
UNION ALL
SELECT * FROM pedido35_39
UNION ALL
SELECT * FROM pedido40_44
UNION ALL
SELECT * FROM pedido45_49;

SELECT table_name
FROM information_schema.tables
WHERE table_schema = 'pedidodiario';
